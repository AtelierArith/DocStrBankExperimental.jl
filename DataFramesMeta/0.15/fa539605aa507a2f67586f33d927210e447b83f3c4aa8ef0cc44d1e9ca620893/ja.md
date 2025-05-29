```
@rselect(x, args...; kwargs...)
```

`@select`の行単位バージョン、すなわちすべての操作はデフォルトで`@byrow`を使用します。詳細については[`@select`](@ref)を参照してください。

### 例

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(x = 1:5, y = 10:14)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     10
   2 │     2     11
   3 │     3     12
   4 │     4     13
   5 │     5     14

julia> @rselect(df, :x, :A = mod(:y, :x) == 0 ? 99 : :x)
5×2 DataFrame
 Row │ x      A
     │ Int64  Int64
─────┼──────────────
   1 │     1     99
   2 │     2      2
   3 │     3     99
   4 │     4      4
   5 │     5      5
```
