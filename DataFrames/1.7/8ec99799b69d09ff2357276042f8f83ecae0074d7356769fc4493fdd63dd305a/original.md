```
SubDataFrame{<:AbstractDataFrame, <:AbstractIndex, <:AbstractVector{Int}} <: AbstractDataFrame
```

A view of an `AbstractDataFrame`. It is returned by a call to the `view` function on an `AbstractDataFrame` if a collections of rows and columns are specified.

A `SubDataFrame` is an `AbstractDataFrame`, so expect that most DataFrame functions should work. Such methods include `describe`, `summary`, `nrow`, `size`, `by`, `stack`, and `join`.

If the selection of columns in a parent data frame is passed as `:` (a colon) then `SubDataFrame` will always have all columns from the parent, even if they are added or removed after its creation.

# Examples

```jldoctest
julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),
                      b=repeat([2, 1], outer=[4]),
                      c=1:8)
8×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     2      1      2
   3 │     3      2      3
   4 │     4      1      4
   5 │     1      2      5
   6 │     2      1      6
   7 │     3      2      7
   8 │     4      1      8

julia> sdf1 = view(df, :, 2:3) # column subsetting
8×2 SubDataFrame
 Row │ b      c
     │ Int64  Int64
─────┼──────────────
   1 │     2      1
   2 │     1      2
   3 │     2      3
   4 │     1      4
   5 │     2      5
   6 │     1      6
   7 │     2      7
   8 │     1      8

julia> sdf2 = @view df[end:-1:1, [1, 3]]  # row and column subsetting
8×2 SubDataFrame
 Row │ a      c
     │ Int64  Int64
─────┼──────────────
   1 │     4      8
   2 │     3      7
   3 │     2      6
   4 │     1      5
   5 │     4      4
   6 │     3      3
   7 │     2      2
   8 │     1      1

julia> sdf3 = groupby(df, :a)[1]  # indexing a GroupedDataFrame returns a SubDataFrame
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5
```
