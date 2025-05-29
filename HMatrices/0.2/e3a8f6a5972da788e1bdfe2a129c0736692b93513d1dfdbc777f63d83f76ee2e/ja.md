```
assemble_hmatrix(K::AbstractKernelMatrix[; atol, rank, rtol, kwargs...])
```

`K`の近似を[`HMatrix`](@ref)として構築します。これは、低ランクブロックのための部分ACAアルゴリズムを使用します。オプション引数`atol`、`rank`、および`rtol`は[`PartialACA`](@ref)コンストラクタに渡され、残りのキーワード引数はメインの`assemble_hmatrix`関数に転送されます。
