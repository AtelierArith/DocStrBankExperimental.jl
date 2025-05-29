```
Intersection{N, S1<:LazySet{N}, S2<:LazySet{N}} <: LazySet{N}
```

Type that represents the intersection of two sets.

### Fields

  * `X`     – set
  * `Y`     – set
  * `cache` – internal cache for avoiding recomputation; see            [`IntersectionCache`](@ref)

### Notes

If the arguments of the lazy intersection are half-spaces, the set is simplified to a polyhedron in constraint representation (`HPolyhedron`).

The intersection preserves convexity: if the set arguments are convex, then their intersection is convex as well.

### Examples

Create an expression $Z$ that lazily represents the intersection of two squares $X$ and $Y$:

```jldoctest lazy_intersection
julia> X, Y = BallInf([0.0, 0.0], 0.5), BallInf([1.0, 0.0], 0.75);

julia> Z = X ∩ Y;

julia> typeof(Z)
Intersection{Float64, BallInf{Float64, Vector{Float64}}, BallInf{Float64, Vector{Float64}}}

julia> dim(Z)
2
```

We can check if the intersection is empty with `isempty`:

```jldoctest lazy_intersection
julia> isempty(Z)
false
```

Do not confuse `Intersection` with the concrete operation, which is computed with the lowercase `intersection` function:

```jldoctest lazy_intersection
julia> W = intersection(X, Y)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([0.375, 0.0], [0.125, 0.5])
```
