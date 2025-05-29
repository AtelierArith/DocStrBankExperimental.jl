```
allowmissing(df::AbstractDataFrame, cols=:)
```

データフレーム `df` のコピーを返し、列 `cols` を要素型 `Union{T, Missing}` に変換して欠損値をサポートできるようにします。

`cols` は任意の列セレクタ（`Symbol`、文字列または整数; `:`, `Cols`, `All`, `Between`, `Not`, 正規表現、または `Symbol`、文字列または整数のベクター）を指定できます。

`cols` が省略された場合、データフレーム内のすべての列が変換されます。

メタデータ: この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(a=[1, 2])
2×1 DataFrame
 Row │ a
     │ Int64
─────┼───────
   1 │     1
   2 │     2

julia> allowmissing(df)
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼────────
   1 │      1
   2 │      2
```
