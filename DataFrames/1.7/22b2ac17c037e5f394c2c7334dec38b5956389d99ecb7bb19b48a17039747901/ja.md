```
disallowmissing(df::AbstractDataFrame, cols=:; error::Bool=true)
```

データフレーム `df` のコピーを返し、列 `cols` を要素型 `Union{T, Missing}` から `T` に変換して、欠損値のサポートを削除します。

`cols` は任意の列セレクタ（`Symbol`、文字列または整数； `:`、`Cols`、`All`、`Between`、`Not`、正規表現、または `Symbol`、文字列または整数のベクター）を指定できます。

`cols` が省略された場合、データフレーム内のすべての列が変換されます。

`error=false` の場合、`missing` 値を含む列はエラーをスローする代わりにスキップされます。

メタデータ：この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df = DataFrame(a=Union{Int, Missing}[1, 2])
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼────────
   1 │      1
   2 │      2

julia> disallowmissing(df)
2×1 DataFrame
 Row │ a
     │ Int64
─────┼───────
   1 │     1
   2 │     2

julia> df = DataFrame(a=[1, missing])
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼─────────
   1 │       1
   2 │ missing

julia> disallowmissing(df, error=false)
2×1 DataFrame
 Row │ a
     │ Int64?
─────┼─────────
   1 │       1
   2 │ missing
```
