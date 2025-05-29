```
cellrows(cols::VecColumnTable, refrows::IdDict)
```

A utility function for processing the object `refrows` returned by [`findcell`](@ref). Unique row values from `cols` corresponding to the keys in `refrows` are sorted lexicographically and stored as rows in a new `VecColumnTable`. Groups of row indices from the values of `refrows` are permuted to match the order of row values and collected in a `Vector`.

# Returns

  * `cells::VecColumnTable`: unique row values from columns in `cols`.
  * `rows::Vector{Vector{Int}}`: row indices for each combination.
