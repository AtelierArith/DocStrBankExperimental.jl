```
hessian(expression::Node, variable_order::AbstractVector{<:Node})
```

Returns the dense symbolic Hessian matrix.

# Example

```julia
julia> @variables x y

julia> hessian(x^2*y^2,[x,y])
2×2 Matrix{FastDifferentiation.Node}:
 (2 * (y ^ 2))  (4 * (y * x))
 (4 * (x * y))  (2 * (x ^ 2))
```
