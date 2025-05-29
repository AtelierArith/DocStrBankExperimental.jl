```
delete_matrix!(
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [must_exist::Bool = true,
    relayout::Bool = true]
)::Nothing
```

`daf`から特定の`rows_axis`と`columns_axis`に対して、特定の`name`を持つ行列プロパティを削除します。

`relayout`（デフォルトの場合）を指定すると、他のレイアウト（すなわち、軸が反転したもの）でも行列が削除されます。

最初に`rows_axis`と`columns_axis`が`daf`に存在することを確認します。`must_exist`（デフォルトの場合）を指定すると、`rows_axis`と`columns_axis`に対して`name`行列が存在することも確認します。
