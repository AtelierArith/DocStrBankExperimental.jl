```
oscar_branch(branch::AbstractString; <keyword arguments>)
oscar_branch(pkgs::Array{String}, branch::AbstractString; <keyword arguments>)
```

For each of the Oscar packages given in `pkgs` create a new local branch named `branch` with start point `start`, in the working copies under the current development directory given via `dir`. If no `pkgs` array is given it will run on all subdirectories of `dir`.

If the directory `dir` does not exist and `pkgs is given it will checkout all`pkgs`first by calling [`oscar_develop`](@ref).

# Arguments

  * `pkgs::Array{String}`: list of packages to operate on, please omit the `.jl`.
  * `branch::String`: new branch name.
  * `dir="oscar-dev"`: development subdirectory.
  * `start="origin/master"`: start point for the branches, use `HEAD` for the current                          head in each directory.
