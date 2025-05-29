```
leftjoin(d1::DTable, d2; on=nothing, l_sorted=false, r_sorted=false, r_unique=false, lookup=nothing)
```

Perform a left join of `d1` with any `Tables.jl` compatible table type. Returns a `DTable` with the result.

If the underlying table type happens to have a `leftjoin` implementation and none of the below `DTable` related kwargs will be provided the specialized function will be used. A good example of that is calling `leftjoin` on a `DTable` with a `DataFrame` underlying type and a `d2` of `DataFrame` type.

# Keyword arguments

  * `on`: Column symbols to join on. Can be provided as a symbol or a pair of symbols in case the column names differ. For joins on multiple columns a vector of the previously mentioned can be provided.
  * `l_sorted`: To indicate the left table is sorted - only useful if the `r_sorted` is set to `true` as well.
  * `r_sorted`: To indicate the right table is sorted.
  * `r_unique`: To indicate the right table only contains unique keys.
  * `lookup`: To provide a dict-like structure that will allow for direct matching of inner rows. The structure needs to contain keys in form of a `Tuple` and values in form of type `Vector{UInt}` containing the related row indices.
