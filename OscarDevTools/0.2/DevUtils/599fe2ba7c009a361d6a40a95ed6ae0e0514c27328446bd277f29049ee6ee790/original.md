```
oscar_update(; <keyword arguments>)
```

For each Oscar package in `dir` fetch all remotes and do a fast forward merge with the currently tracked upstream branch. Similiar to doing `git pull --ff-only` in each directory.

# Arguments

  * `dir="oscar-dev"`: development subdirectory.
