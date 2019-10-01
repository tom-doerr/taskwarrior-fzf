# Taskwarrior fzf interface

An [fzf](https://github.com/junegunn/fzf) based UI for [taskwarrior](https://taskwarrior.org/), implemented as a `/bin/sh` script.

## Install

Link / Copy / Move the file `taskfzf` from this repo to your `$PATH`.

## Usage

### Command Line Arguments

Launching `taskfzf`, will present you an `fzf` interface where every task is
a line you can filter out using `fzf`'s magical search.

Without arguments, you'll see the list of tasks `task` would list if given no
arguments. 

You can supply a "report" argument (e.g `ls`, `list`, `next`..) to `taskfzf` as
you'd supply `task`.

Besides that, `taskfzf` also accepts modifications to your config using `rc.`
arguments given right before the optional report argument.

### Key Bindings

`taskfzf` uses [`fzf`'s bindings](https://www.mankier.com/1/fzf#Key_Bindings)
to perform actions over the highlighted task or to change the list of tasks
presented. Since tasks are usually written in lower case letters, and in order
to mitigate key bindings clashes with a parent program `taskfzf` may run inside
(e.g tmux, Neovim's `:term` etc.), I decided to bind every upper case letter to
an action.

#### Perform an action over the selected tasks

- `D` marks the tasks as done (`task do`).
- <kbd>Delete</kbd> Deletes the tasks (`task del`).
- `U` undo the last action performed (`task undo`).
- `E` edits the task in your editor (`task edit`).
- `A` appends a text to the tasks using a shell input (`task append`).
- `M` modifies a task using a shell input (`task modify`).

#### Change the current list of tasks

Each of the following key bindings changes the list of tasks you can perform
the actions from above by changing the context (`rc.context`) or the "report".

Choosing a different context/report is also performed by `fzf` and the
candidates are from `task reports` or `task contexts`.

- `R` changes the current "report" (`task reports`).
- `C` changes the current context (`task contexts`).
