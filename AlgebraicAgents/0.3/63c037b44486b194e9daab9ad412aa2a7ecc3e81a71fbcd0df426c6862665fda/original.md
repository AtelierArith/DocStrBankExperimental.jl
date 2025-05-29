```
getagent(agent::AbstractAlgebraicAgent, path::Union{Glob.FilenameMatch, Regex})
```

Get an agent given a regex or glob string.

## Examples

```julia
getagent(a, r"agent.*")
getagent(a, glob"**/agent/")
```
