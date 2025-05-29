```
DataFrameRow{<:AbstractDataFrame, <:AbstractIndex}
```

A view of one row of an `AbstractDataFrame`.

A `DataFrameRow` is returned by `getindex` or `view` functions when one row and a selection of columns are requested, or when iterating the result of the call to the [`eachrow`](@ref) function.

The `DataFrameRow` constructor can also be called directly:

```
DataFrameRow(parent::AbstractDataFrame, row::Integer, cols=:)
```

A `DataFrameRow` supports the iteration interface and can therefore be passed to functions that expect a collection as an argument. Its element type is always `Any`.

Indexing is one-dimensional like specifying a column of a `DataFrame`. You can also access the data in a `DataFrameRow` using the `getproperty` and `setproperty!` functions and convert it to a `Tuple`, `NamedTuple`, or `Vector` using the corresponding functions.

If the selection of columns in a parent data frame is passed as `:` (a colon) then `DataFrameRow` will always have all columns from the parent, even if they are added or removed after its creation.

# Examples

```jldoctest
julia> df = DataFrame(a=repeat([1, 2], outer=[2]),
                      b=repeat(["a", "b"], inner=[2]),
                      c=1:4)
4×3 DataFrame
 Row │ a      b       c
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  a           1
   2 │     2  a           2
   3 │     1  b           3
   4 │     2  b           4

julia> df[1, :]
DataFrameRow
 Row │ a      b       c
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  a           1

julia> @view df[end, [:a]]
DataFrameRow
 Row │ a
     │ Int64
─────┼───────
   4 │     2

julia> eachrow(df)[1]
DataFrameRow
 Row │ a      b       c
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  a           1

julia> Tuple(df[1, :])
(1, "a", 1)

julia> NamedTuple(df[1, :])
(a = 1, b = "a", c = 1)

julia> Vector(df[1, :])
3-element Vector{Any}:
 1
  "a"
 1
```
