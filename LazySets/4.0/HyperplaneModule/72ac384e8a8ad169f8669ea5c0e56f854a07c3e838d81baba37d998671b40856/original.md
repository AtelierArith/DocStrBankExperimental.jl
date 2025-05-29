```
Hyperplane{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

Type that represents a hyperplane of the form $a⋅x = b$.

### Fields

  * `a` – normal direction (non-zero)
  * `b` – constraint

### Examples

The plane $y = 0$:

```jldoctest
julia> Hyperplane([0, 1.], 0.)
Hyperplane{Float64, Vector{Float64}}([0.0, 1.0], 0.0)
```
