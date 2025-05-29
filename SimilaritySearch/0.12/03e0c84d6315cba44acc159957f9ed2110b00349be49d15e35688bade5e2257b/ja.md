```
struct StrideMatrixDatabase{M<:StrideArray} <: AbstractDatabase

StrideMatrixDatabase(matrix::StrideArray)
```

`StrideArray`に行列オブジェクトをラップし、データベースとしてラップします。一般的な使用法については[`AbstractDatabase`](@ref)を参照してください。
