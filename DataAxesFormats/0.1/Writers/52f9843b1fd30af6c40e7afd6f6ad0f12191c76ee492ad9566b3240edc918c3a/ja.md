```
set_matrix!(
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    matrix::Union{StorageReal, StorageMatrix};
    [overwrite::Bool = false,
    relayout::Bool = true]
)::Nothing
```

`daf`の`rows_axis`と`columns_axis`のためにいくつかの`name`で行列プロパティを設定します。これはJuliaなので、これは列優先の`matrix`である必要があります。

指定された`matrix`が実際に[`StorageScalar`](@ref)である場合、保存された行列はこの値で埋められます。

`relayout`（デフォルト）を指定すると、これは自動的に行列を[`relayout!`](@ref)し、結果を保存します。したがって、データは行優先レイアウト（つまり、軸が反転した状態）でも保存され、[`relayout_matrix!`](@ref)を呼び出すのと同様になります。

最初に、`rows_axis`と`columns_axis`が`daf`に存在すること、`matrix`が適切なサイズの列優先であることを確認します。`overwrite`（デフォルト）でない場合、`name`行列が`rows_axis`と`columns_axis`のために存在しないことも確認します。
