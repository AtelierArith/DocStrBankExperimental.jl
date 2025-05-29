```julia
printstatus(io::IO, r::GitOut.Repo; ...)
printstatus(io::IO, r::GitOut.Repo, pathspec; kw...)

```

Prints the status as it would be returned by command line `git status`.  Additional arguments are passed to [`rawstatus`](@ref)
