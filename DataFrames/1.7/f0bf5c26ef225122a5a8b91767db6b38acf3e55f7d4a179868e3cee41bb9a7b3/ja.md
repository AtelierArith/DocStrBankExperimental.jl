```
fillcombinations(df::AbstractDataFrame, indexcols;
                     allowduplicates::Bool=false,
                     fill=missing)
```

データフレーム `df` の列 `indexcols` のレベルのすべての組み合わせを生成します。レベルとその順序は `levels` 関数によって決定されます（すなわち、デフォルトでは辞書式にソートされたユニークな値、または例えば `CategoricalArray` 列のためのカスタムレベルのセット）、さらに `missing` が存在する場合はそれも含まれます。

`df` に存在しない `indexcols` の組み合わせについては、これらの列は `fill` 値（デフォルトでは `missing`）で埋められます。

`allowduplicates=false`（デフォルト）である場合、`indexcols` は `indexcols` 値のユニークな組み合わせのみを含むことができます。`allowduplicates=true` の場合は、重複が許可されます。

メタデータ: この関数はテーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(x=1:2, y='a':'b', z=["x", "y"])
2×3 DataFrame
 Row │ x      y     z
     │ Int64  Char  String
─────┼─────────────────────
   1 │     1  a     x
   2 │     2  b     y

julia> fillcombinations(df, [:x, :y])
4×3 DataFrame
 Row │ x      y     z
     │ Int64  Char  String?
─────┼──────────────────────
   1 │     1  a     x
   2 │     2  a     missing
   3 │     1  b     missing
   4 │     2  b     y

julia> fillcombinations(df, [:y, :z], fill=0)
4×3 DataFrame
 Row │ x       y     z
     │ Int64?  Char  String
─────┼──────────────────────
   1 │      1  a     x
   2 │      0  b     x
   3 │      0  a     y
   4 │      2  b     y
```
