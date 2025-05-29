```
HPolyhedron{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

Type that represents a convex polyhedron in constraint representation, that is, a finite intersection of half-spaces,

$$
P = ⋂_{i = 1}^m H_i,
$$

where each $H_i = \{x ∈ ℝ^n : a_i^T x ≤ b_i \}$ is a half-space, $a_i ∈ ℝ^n$ is the normal vector of the $i$-th half-space and $b_i$ is the displacement. The set $P$ may or may not be bounded (see also [`HPolytope`](@ref), which assumes boundedness).

### Fields

  * `constraints` – vector of linear constraints
