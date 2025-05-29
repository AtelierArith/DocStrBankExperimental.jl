```
repeat!(df::DataFrame; inner::Integer=1, outer::Integer=1)
```

データフレーム `df` の行を繰り返すことで、インプレースで更新します。`inner` は各行が繰り返される回数を指定し、`outer` は全行セットが繰り返される回数を指定します。`df` の列は新たに割り当てられます。

メタデータ: この関数はテーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(a=1:2, b=3:4)
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4

julia> repeat!(df, inner=2, outer=3);

julia> df
12×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     1      3
   3 │     2      4
   4 │     2      4
   5 │     1      3
   6 │     1      3
   7 │     2      4
   8 │     2      4
   9 │     1      3
  10 │     1      3
  11 │     2      4
  12 │     2      4
```
