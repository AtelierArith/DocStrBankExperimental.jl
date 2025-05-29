```
order(col::ColumnIndex; kwargs...)
```

Specify sorting order for a column `col` in a data frame. `kwargs` can be `lt`, `by`, `rev`, and `order` with values following the rules defined in [`sort!`](@ref).

See also: [`sort!`](@ref), [`sort`](@ref)

# Examples

```jldoctest
julia> df = DataFrame(x=[-3, -1, 0, 2, 4], y=1:5)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │    -3      1
   2 │    -1      2
   3 │     0      3
   4 │     2      4
   5 │     4      5

julia> sort(df, order(:x, rev=true))
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     4      5
   2 │     2      4
   3 │     0      3
   4 │    -1      2
   5 │    -3      1

julia> sort(df, order(:x, by=abs))
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     0      3
   2 │    -1      2
   3 │     2      4
   4 │    -3      1
   5 │     4      5
```
