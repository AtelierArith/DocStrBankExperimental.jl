```
UnresolveableIdentifier{T}(identifier::Union{String, UUID}, [collection::DataCollection])
```

No `T` (optionally from `collection`) could be found that matches `identifier`.

# Example occurrences

```julia-repl
julia> d"iirs"
ERROR: UnresolveableIdentifier: "iirs" does not match any available data sets
  Did you perhaps mean to refer to one of these data sets?
    ■:iris (75% match)
Stacktrace: [...]

julia> d"iris::Int"
ERROR: UnresolveableIdentifier: "iris::Int" does not match any available data sets
  Without the type restriction, however, the following data sets match:
    dataset:iris, which is available as a DataFrame, Matrix, CSV.File
Stacktrace: [...]
```
