```
HPolytope{N, VN<:AbstractVector{N}} <: AbstractPolytope{N}
```

Type that represents a convex polytope in constraint representation, i.e., a bounded set characterized by a finite intersection of half-spaces,

$$
P = ⋂_{i = 1}^m H_i,
$$

where each $H_i = \{x ∈ ℝ^n : a_i^T x ≤ b_i \}$ is a half-space, $a_i ∈ ℝ^n$ is the normal vector of the $i$-th half-space and $b_i$ is the displacement. It is assumed that $P$ is bounded (see also [`LazySets.HPolyhedron`](@ref), which does not make such an assumption).

### Fields

  * `constraints`       – vector of linear constraints
  * `check_boundedness` – (optional, default: `false`) flag for checking if the                        constraints make the polytope bounded; (boundedness is                        a running assumption for this type)

### Notes

A polytope is a bounded polyhedron.

Boundedness is a running assumption for this type. For performance reasons, boundedness is not checked in the constructor by default. We also exploit this assumption, so a boundedness check may not return the answer you would expect.

```jldoctest isbounded
julia> P = HPolytope([HalfSpace([1.0], 1.0)]);  # x <= 1

julia> isbounded(P)  # uses the type assumption and does not actually check
true

julia> isbounded(P, false)  # performs a real boundedness check
false
```
