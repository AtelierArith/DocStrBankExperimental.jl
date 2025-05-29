```
rdistinct!(d, args...)
```

`@distinct!`の行ごとのバージョン、すなわちすべての操作はデフォルトで`@byrow`を使用します。詳細については[`@distinct!`](@ref)を参照してください。

### 例

```julia
julia> using DataFramesMeta

julia> df = DataFrame(x = 1:5, y = 5:-1:1)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     5
   2 │     2     4
   3 │     3     3
   4 │     4     2
   5 │     5     1
   
julia> @rdistinct!(df, :x + :y)
5×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     5
```
