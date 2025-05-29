```
@rtransform(x, args...; kwargs...)
```

`@transform`の行単位バージョン、すなわちすべての操作はデフォルトで`@byrow`を使用します。詳細については[`@transform`](@ref)を参照してください。

### 例

```jldoctest
julia> using DataFramesMeta

julia> df = DataFrame(x = 1:5, y = 11:15)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @rtransform(df, :a = :x + :y ^ 2, :c = :y == 13 ? 999 : 1 - :y)
5×4 DataFrame
 Row │ x      y      a      c
     │ Int64  Int64  Int64  Int64
─────┼────────────────────────────
   1 │     1     11    122    -10
   2 │     2     12    146    -11
   3 │     3     13    172    999
   4 │     4     14    200    -13
   5 │     5     15    230    -14
```
