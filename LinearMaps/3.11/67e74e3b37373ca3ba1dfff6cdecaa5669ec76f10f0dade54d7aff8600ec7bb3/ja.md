```
*(x::LinearAlgebra.AdjointAbsVec, A::LinearMap)::AdjointAbsVec
```

線形写像 `A` の右作用を隣接ベクトル `x` に対して計算し、隣接ベクトルを返します。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); x=[1.0, 1.0]; x'A
1×2 adjoint(::Vector{Float64}) with eltype Float64:
 4.0  6.0
```
