```
deleteat!(df::DataFrame, inds)
```

`DataFrame` `df` から `inds` で指定された行をインプレースで削除し、返します。

内部的に `deleteat!` はすべての列に対して呼び出されるため、`inds` は次のいずれかでなければなりません: ソートされていてユニークな整数のベクター、ブールベクター、整数、または有効なセレクタをラップした `Not`。

メタデータ: この関数はテーブルレベルおよびカラムレベルの `:note` スタイルのメタデータを保持します。

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

julia> deleteat!(df, 2)
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      4
   2 │     3      6
```
