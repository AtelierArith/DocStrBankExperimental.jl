```julia
git(r::GitOut.Repo; ...) -> Cmd
git(r::GitOut.Repo, args; kw...) -> Cmd

```

Create a `Cmd` object for running a git command for the repo `r`.  Additional keyword arguments are passed to [`git`](@ref). 
