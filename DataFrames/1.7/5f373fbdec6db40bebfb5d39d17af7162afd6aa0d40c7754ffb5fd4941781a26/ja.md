```
disallowmissing!(df::DataFrame, cols=:; error::Bool=true)
```

データフレーム `df` の列 `cols` を要素型 `Union{T, Missing}` から `T` に変換し、欠損値のサポートを削除します。

`cols` は任意の列セレクタ（`Symbol`、文字列または整数； `:`、`Cols`、`All`、`Between`、`Not`、正規表現、または `Symbol`、文字列または整数のベクター）を指定できます。

`cols` が省略された場合、データフレーム内のすべての列が変換されます。

`error=false` の場合、`missing` 値を含む列はエラーをスローする代わりにスキップされます。

メタデータ：この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。
