```
resize!(df::DataFrame, n::Integer)
```

`df`を`n`行にリサイズするために、`df`のすべての列に対して`resize!`を呼び出します。

メタデータ: この関数は、テーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(a=1:3, b=4:6)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      4
   2 │     2      5
   3 │     3      6

julia> resize!(df, 2)
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      4
   2 │     2      5
```
