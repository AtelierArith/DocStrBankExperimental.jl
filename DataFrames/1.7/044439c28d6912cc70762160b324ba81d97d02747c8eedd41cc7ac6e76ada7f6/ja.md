```
order(col::ColumnIndex; kwargs...)
```

データフレームの列 `col` のソート順を指定します。`kwargs` には `lt`、`by`、`rev`、および `order` が含まれ、値は [`sort!`](@ref) で定義されたルールに従います。

参照: [`sort!`](@ref)、[`sort`](@ref)

# 例

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
