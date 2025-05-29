```
empty_dense_vector!(
    fill::Function,
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal};
    [overwrite::Bool = false]
)::Any
```

`daf`内の`axis`に対して`name`という名前の空の密ベクトルプロパティを作成し、`fill`に渡して結果を返します。

返されるベクトルは初期化されていません; 呼び出し元はそれに値を`fill`することが期待されています。これは、データに設定する前にベクトルのコピーを作成するのを避けるため、ディスク上でベクトルを作成する際に大きな違いを生み出します（メモリマッピングを使用）。この理由から、文字列には固定サイズがないため、これは機能しません。

最初に、`axis`が`daf`に存在することと、プロパティ名が`name`でないことを確認します。`overwrite`（デフォルト）でない場合、これにより`axis`に対して`name`ベクトルが存在しないことも確認されます。
