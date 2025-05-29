```
get_year_idxs(data, year_idxs) -> idxs
```

Converts `year_idxs` into a usable set of indices that can index into `get_years(data)`.  `year_idxs` can be any of the following types:

  * `Colon`
  * `Int64`
  * `AbstractVector{Int64}`
  * `AbstractString` - Representing the year, i.e. "y2020"
  * `AbstractVector{<:AbstractString}` - a vector of strings representing the year, i.e. "y2020"
  * `Tuple{<:AbstractString, <:AbstractString}`
  * `Function` - a function of the year string that returns a boolean.  I.e. <=("y2030")
