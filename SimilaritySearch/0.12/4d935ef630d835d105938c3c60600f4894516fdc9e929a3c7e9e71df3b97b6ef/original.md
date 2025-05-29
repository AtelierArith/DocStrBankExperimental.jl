```
loadindex(filename::AbstractString, db::Union{Nothing,AbstractDatabase}=nothing; kwargs...)
```

Loads an index from `filename`. If `db` is given it will replace the dataset on the loaded index

# Arguments

  * `db`: Replaces the index database after loading with that specified in `db`
  * `parent="/"`: Parent group of the index
