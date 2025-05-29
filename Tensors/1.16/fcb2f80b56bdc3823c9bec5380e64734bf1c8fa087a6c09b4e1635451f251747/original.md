```
rotate(x::AbstractTensor{2}, θ::Number)
```

Rotate a two dimensional tensor `x` `θ` radians around the out-of-plane axis.

# Examples

```jldoctest
julia> x = Vec{2}((0.0, 1.0));

julia> rotate(x, π/4)
2-element Vec{2, Float64}:
 -0.7071067811865475
  0.7071067811865476
```
