```
empty!(df::DataFrame)
```

`df`からすべての行を削除し、各列を空にします。

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

julia> empty!(df)
0×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┴──────────────

julia> df.a, df.b
(Int64[], Int64[])
```
