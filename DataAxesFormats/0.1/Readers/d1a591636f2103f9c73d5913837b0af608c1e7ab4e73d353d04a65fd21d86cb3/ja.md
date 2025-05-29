```
has_matrix(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [relayout::Bool = true]
)::Bool
```

`daf`において、`rows_axis`と`columns_axis`のために指定された`name`を持つ行列プロパティが存在するかどうかを確認します。これはJuliaであるため、列優先の行列を意味します。`daf`は同じデータの2つのコピーを含む場合があり、その場合、両方の軸順序で行列を報告します。

`relayout`（デフォルト）を指定した場合、データが他のレイアウト（すなわち、軸が反転した状態）に存在するかどうかも確認します。

最初に、`rows_axis`と`columns_axis`が`daf`に存在することを確認します。
