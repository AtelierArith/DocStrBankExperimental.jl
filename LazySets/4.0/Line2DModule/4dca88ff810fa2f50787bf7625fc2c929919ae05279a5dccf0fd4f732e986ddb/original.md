```
Line2D{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

Type that represents a line in 2D of the form $a⋅x = b$ (i.e., a special case of a `Hyperplane`).

### Fields

  * `a` – normal direction (non-zero)
  * `b` – constraint

### Examples

The line $y = -x + 1$:

```jldoctest
julia> Line2D([1., 1.], 1.)
Line2D{Float64, Vector{Float64}}([1.0, 1.0], 1.0)
```

The alternative constructor takes two 2D points (`AbstractVector`s) `p` and `q` and creates a canonical line from `p` to `q`. See the algorithm section below for details.

```jldoctest
julia> Line2D([1., 1.], [2., 2])
Line2D{Float64, Vector{Float64}}([-1.0, 1.0], 0.0)
```

### Algorithm

Given two points $p = (x₁, y₁)$ and $q = (x₂, y₂)$, the line that passes through these points is

$$
ℓ:~~y - y₁ = \dfrac{(y₂ - y₁)}{(x₂ - x₁)} ⋅ (x-x₁).
$$

The particular case $x₂ = x₁$ defines a line parallel to the $y$-axis (vertical line).
