```
*(x::LinearAlgebra.TransposeAbsVec, A::LinearMap)::TransposeAbsVec
```

線形写像 `A` の右作用を転置ベクトル `x` に対して計算し、転置ベクトルを返します。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); x=[1.0, 1.0]; transpose(x)*A
1×2 transpose(::Vector{Float64}) with eltype Float64:
 4.0  6.0
```
