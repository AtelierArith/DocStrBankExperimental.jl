```
*(A::LinearMap, x::AbstractVector)::AbstractVector
```

線形写像 `A` がベクトル `x` に作用するのを計算します。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); x=[1.0, 1.0];

julia> A*x
2-element Vector{Float64}:
 3.0
 7.0

julia> A(x)
2-element Vector{Float64}:
 3.0
 7.0
```
