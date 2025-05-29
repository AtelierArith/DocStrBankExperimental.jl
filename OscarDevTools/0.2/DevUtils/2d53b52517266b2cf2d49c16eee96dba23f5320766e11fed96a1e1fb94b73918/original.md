```
oscar_add_remotes(fork::String; <keyword arguments>)
oscar_add_remotes(pkgs::Array{String}, fork::String; <keyword arguments>)
```

For each Oscar package in `pkgs` (or existing in `dir` if `pkgs` is not given) add a new git remote for `https://github.com/fork/PackageName.jl`. The push-url is set to `git@github.com:fork/PackageName.jl` to facilitate pushing via ssh.

# Arguments

  * `pkgs::Array{String}`: list of packages to operate on, please omit the `.jl`.
  * `fork::String`: github organisation/user for new remote
  * `dir="oscar-dev"`: development subdirectory.
