```
start_assemble(K::AbstractSparseMatrixCSC;            fillzero::Bool=true) -> CSCAssembler
start_assemble(K::AbstractSparseMatrixCSC, f::Vector; fillzero::Bool=true) -> CSCAssembler
```

行列 `K` とオプションのベクトル `f` から `CSCAssembler` を作成します。

```
start_assemble(K::Symmetric{AbstractSparseMatrixCSC};                 fillzero::Bool=true) -> SymmetricCSCAssembler
start_assemble(K::Symmetric{AbstractSparseMatrixCSC}, f::Vector=Td[]; fillzero::Bool=true) -> SymmetricCSCAssembler
```

行列 `K` とオプションのベクトル `f` から `SymmetricCSCAssembler` を作成します。

`CSCAssembler` と `SymmetricCSCAssembler` は、効率的な行列アセンブリに必要な作業領域を割り当てます。要素からの寄与を組み立てるには、[`assemble!`](@ref) を使用します。

キーワード引数 `fillzero` は、`K` と `f` をゼロにする必要がない場合、現在の値を保持するために `false` に設定できます。
