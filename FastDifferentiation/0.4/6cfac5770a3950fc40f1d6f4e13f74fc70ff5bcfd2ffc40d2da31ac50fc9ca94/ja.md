```
derivative(A::AbstractArray{<:Node}, variables...)
```

`∂A/(∂variables[1],...,∂variables[n])` を計算します。ヤコビ行列の異なる列を計算するのではなく、繰り返し微分を行います。

# 例

```julia
julia> A = [t t^2;3t^2 5]  
2×2 Matrix{Node}:
 t              (t ^ 2)
 (3 * (t ^ 2))  5

julia> derivative(A,t)  
2×2 Matrix{Node}:
 1.0      (2 * t)
 (6 * t)  0.0

julia> derivative(A,t,t)  
2×2 Matrix{Node{T, 0} where T}:
 0.0  2
 6    0.0
```
