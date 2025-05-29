```
empty_dense_matrix!(
    fill::Function,
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal};
    [overwrite::Bool = false]
)::Any
```

`daf`の`rows_axis`と`columns_axis`のために、いくつかの`name`を持つ空の密行列プロパティを作成し、それを`fill`に渡して結果を返します。これはJuliaなので、これは列優先の`matrix`になります。

返される行列は初期化されていません; 呼び出し元はそれに値を`fill`することが期待されています。これは、`daf`に設定する前に行列のコピーを作成するのを避けるため、ディスク上で行列を作成する際に大きな違いを生み出します（メモリマッピングを使用）。この理由から、文字列には固定サイズがないため、これは機能しません。

最初に、`rows_axis`と`columns_axis`が`daf`に存在することを確認し、`matrix`が適切なサイズの列優先であることを確認します。`overwrite`（デフォルト）でない場合、これにより、`rows_axis`と`columns_axis`のために`name`行列が存在しないことも確認されます。
