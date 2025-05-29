```
struct MatrixDatabase{M<:AbstractDatabase} <: AbstractDatabase

MatrixDatabase(matrix::AbstractMatrix)
```

行列のようなオブジェクト `matrix` を `MatrixDatabase` にラップします。一般的な使用法については [`AbstractDatabase`](@ref) を参照してください。
