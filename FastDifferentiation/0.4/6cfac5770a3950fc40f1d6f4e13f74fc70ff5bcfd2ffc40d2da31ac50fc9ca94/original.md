```
derivative(A::AbstractArray{<:Node}, variables...)
```

Computes `∂A/(∂variables[1],...,∂variables[n])`. Repeated differentiation rather than computing different columns of the Jacobian.

# Example

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
