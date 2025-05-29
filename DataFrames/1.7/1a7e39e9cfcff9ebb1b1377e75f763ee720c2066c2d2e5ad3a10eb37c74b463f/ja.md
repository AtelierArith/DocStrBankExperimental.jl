```
repeat!(df::DataFrame, count::Integer)
```

データフレーム `df` を、指定された回数 `count` だけ行を繰り返すことでインプレースで更新します。`df` の列は新たに割り当てられます。

メタデータ: この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(a=1:2, b=3:4)
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4

julia> repeat(df, 2)
4×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4
   3 │     1      3
   4 │     2      4
```
