```
iso_id([db::SQLite.DB,] M::T, I::T) where T <: Union{Integer, AbstractVector{Integer}}
```

Returns the global isotopologue IDs for the given molecule ids and local ids provided either as single value or as array for both parameters.

# Arguments

  * `M`: molecule id or array of ids
  * `I`: local isotopologue id or array of ids
