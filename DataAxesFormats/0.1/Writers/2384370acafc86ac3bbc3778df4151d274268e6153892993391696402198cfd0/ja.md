```
empty_sparse_matrix!(
    fill::Function,
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal},
    nnz::StorageInteger,
    intdype::Maybe{Type{<:StorageInteger}} = nothing;
    [overwrite::Bool = false]
)::Any
```

`daf`の`rows_axis`と`columns_axis`のために`name`を持つ空の疎行列プロパティを作成し、その部分（`colptr`、`rowval`、および`nzval`）を`fill`に渡し、結果を返します。

`indtype`が指定されていない場合、行列に必要な最小の符号なし整数型が自動的に選択されます。

返される行列は初期化されていません。呼び出し元は`colptr`、`rowval`、および`nzval`ベクターを`fill`することが期待されています。`nnz`を指定することで、サイズが事前に知られるため、ディスクスペースの事前割り当てが可能になります。この理由から、文字列には固定サイズがないため、これは機能しません。

これはこの関数の有用性を大きく制限します。通常、`nnz`は行列を完全に計算した後にのみ知られるからです。それでも、いくつかのケースでは、いくつかの小さな行列を連結することによって大きな疎行列が作成されます。この関数は、メモリマップドディスクフォーマットの場合にコピーを避けてデータに直接行うことを可能にします。

!!! warning
    呼び出し元は、3つのベクターに有効なデータを埋める責任があります。具体的には、次のことを確認する必要があります：

      * `colptr[1] == 1`
      * `colptr[end] == nnz + 1`
      * `colptr[i] <= colptr[i + 1]`
      * すべての`j`について、すべての`i`に対して`colptr[j] <= i`かつ`i + 1 < colptr[j + 1]`である場合、`1 <= rowptr[i] < rowptr[i + 1] <= nrows`


これは最初に`rows_axis`と`columns_axis`が`daf`に存在することを確認します。`overwrite`（デフォルト）でない場合、これはまた`rows_axis`と`columns_axis`のために`name`行列が存在しないことを確認します。
