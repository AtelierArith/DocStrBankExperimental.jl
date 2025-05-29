```
PackedVectorOfVectors{P,V,E} <: AbstractVector{E}
```

ベクトルのベクトルで、単一の長いベクトル `v::V` とサブベクトルの境界を示すポインタのベクトル `p::P` として格納されます。

`PackedVectorOfVectors` は、`rowval` ベクトルなしの `SparseMatrixCSC` にほぼ相当します。
