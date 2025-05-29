```julia
printstatus(r::GitOut.Repo; ...)
printstatus(r::GitOut.Repo, pathspec; kw...)

```

Prints the status as it would be returned by command line `git status` to `stdout`.  Additional arguments are passed to [`rawstatus`](@ref)
