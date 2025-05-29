```
empty_sparse_vector!(
    fill::Function,
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal},
    nnz::StorageInteger,
    indtype::Maybe{Type{<:StorageInteger}} = nothing;
    [overwrite::Bool = false]
)::Any
```

`daf`の`axis`に対して`name`を持つ空のスパースベクトルプロパティを作成し、その部分（`nzind`と`nzval`）を`fill`に渡して結果を返します。

`indtype`が指定されていない場合、自動的にベクトルに必要な最小の符号なし整数型が選択されます。

返されるベクトルは初期化されていません。呼び出し元は`nzind`と`nzval`ベクトルに値を`fill`することが期待されています。`nnz`を指定することで、サイズが事前に知られるため、ディスクデータの事前割り当てが可能になります。このため、固定サイズを持たない文字列には適用できません。

これはこの関数の有用性を大きく制限します。通常、`nnz`は行列を完全に計算した後にのみ知られます。それでも、いくつかのケースでは、いくつかの小さなベクトルを連結することによって大きなスパースベクトルが作成されます。この関数は、メモリマップドディスクフォーマットの場合にコピーを避けてデータベクトルに直接行うことを可能にします。

!!! warning
    2つのベクトルに有効なデータを埋めるのは呼び出し元の責任です。具体的には、次のことを確認する必要があります：

      * `nzind[1] == 1`
      * `nzind[i] <= nzind[i + 1]`
      * `nzind[end] == nnz`


これは最初に`axis`が`daf`に存在することと、プロパティ名が`name`でないことを確認します。`overwrite`（デフォルト）でない場合、これにより`axis`に対して`name`ベクトルが存在しないことも確認されます。
