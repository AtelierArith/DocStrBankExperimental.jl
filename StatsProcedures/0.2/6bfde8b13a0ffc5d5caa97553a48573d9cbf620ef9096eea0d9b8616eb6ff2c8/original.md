```
StatsStep{Alias, F<:Function, ById}
```

Specification for a step in an [`AbstractStatsProcedure`](@ref). An instance of `StatsStep` is callable.

# Parameters

  * `Alias::Symbol`: alias of the type for pretty-printing.
  * `F<:Function`: type of the function to be called by `StatsStep` with `F.instance`.
  * `ById::Bool`: whether arguments from multiple [`StatsSpec`](@ref)s should be grouped by `object-id` or `isequal`.

# Methods

```
(step::StatsStep{A,F})(ntargs::NamedTuple; verbose::Union{Bool,IO}=false)
```

Call an instance of function of type `F` with arguments extracted from `ntargs` via [`groupargs`](@ref) and [`combinedargs`](@ref).

A message with the name of the `StatsStep` is printed to `stdout` if a keyword `verbose` takes the value `true` or `ntargs` contains a key-value pair `verbose=true`. Alternative `IO` stream can be specified by setting the value of `verbose`. The value from `ntargs` supersedes the keyword argument in case both are specified.

## Returns

  * `NamedTuple`: named intermediate results.
