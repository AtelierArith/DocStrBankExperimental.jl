```
ConvexHull{N, S1<:LazySet{N}, S2<:LazySet{N}} <: ConvexSet{N}
```

Type that represents the convex hull of the union of two sets, i.e., the set

$$
Z = \{z ∈ ℝ^n : z = λx + (1-λ)y,\qquad x ∈ X, y ∈ Y,λ ∈ [0, 1] \}.
$$

### Fields

  * `X` – set
  * `Y` – set

### Notes

The `EmptySet` is the neutral element for `ConvexHull`.

This type is always convex.

### Examples

The convex hull of two 100-dimensional Euclidean balls:

```jldoctest
julia> b1, b2 = Ball2(zeros(100), 0.1), Ball2(4*ones(100), 0.2);

julia> c = ConvexHull(b1, b2);

julia> typeof(c)
ConvexHull{Float64, Ball2{Float64, Vector{Float64}}, Ball2{Float64, Vector{Float64}}}
```
