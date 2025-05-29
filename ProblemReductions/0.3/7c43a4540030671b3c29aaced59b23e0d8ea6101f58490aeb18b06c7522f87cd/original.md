```
flavor_names(::Type{<:AbstractProblem}) -> Vector
```

Returns a vector as the names of the flavors (domain) of a degree of freedom. It falls back to [`flavors`](@ref) if no method is defined. Use `ProblemReductions.name2config` and `ProblemReductions.config2name` to convert between the names and the configuration.
