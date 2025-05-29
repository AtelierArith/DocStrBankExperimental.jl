```
DimTable <: AbstractDimTable

DimTable(A::AbstractDimArray)
```

Construct a Tables.jl/TableTraits.jl compatible object out of an `AbstractDimArray`.

This table will have a column for the array data and columns for each `Dimension` index, as a [`DimColumn`]. These are lazy, and generated as required.

Column names are converted from the dimension types using [`DimensionalData.dim2key`](@ref). This means type `Ti` becomes the column name `:Ti`, and `Dim{:custom}` becomes `:custom`.

To get dimension columns, you can index with `Dimension` (`X()`) or `Dimension` type (`X`) as well as the regular `Int` or `Symbol`.
