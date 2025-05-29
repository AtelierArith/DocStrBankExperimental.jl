```
jacobian(
    terms::AbstractVector{<:Node},
    partial_variables::AbstractVector{<:Node}
)
```

Jacobian matrix of the n element function defined by `terms`. Each term element is a Node expression graph. Only the columns of the Jacobian corresponsing to the elements of `partial_variables` will be computed and the partial columns in the Jacobian matrix will be in the order specified by `partial_variables`. Examples:

```julia
julia> @variables x y

julia> jacobian([x*y,y*x],[x,y])
2×2 Matrix{Node}:
 y  x
 y  x

julia> jacobian([x*y,y*x],[y,x])
2×2 Matrix{Node}:
 x  y
 x  y

julia> jacobian([x*y,y*x],[x])
2×1 Matrix{Node}:
 y
 y
```
