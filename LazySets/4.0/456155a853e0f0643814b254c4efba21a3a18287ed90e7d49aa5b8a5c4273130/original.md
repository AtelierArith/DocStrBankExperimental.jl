```
AbstractZonotope{N} <: AbstractCentrallySymmetricPolytope{N}
```

Abstract type for zonotopic sets.

### Notes

Mathematically, a zonotope is defined as the set

$$
Z = \left\{ c + ∑_{i=1}^p ξ_i g_i,~~ ξ_i ∈ [-1, 1]~~ ∀ i = 1,…, p \right\},
$$

where $c ∈ ℝ^n$ is its center and $\{g_i\}_{i=1}^p$, $g_i ∈ ℝ^n$, is the set of generators. This characterization defines a zonotope as the finite Minkowski sum of line segments. Zonotopes can be equivalently described as the image of a unit infinity-norm ball in $ℝ^n$ by an affine transformation.

See [`Zonotope`](@ref) for a standard implementation of this interface.

Every concrete `AbstractZonotope` must define the following functions:

  * `generators(::AbstractZonotope)` – return an iterator over the generators
  * `genmat(::AbstractZonotope)` – return a generator matrix

Since the functions `genmat` and `generators` can be defined in terms of each other, it is sufficient to only genuinely implement one of them and let the implementation of the other function call the fallback implementation `genmat_fallback` resp. `generators_fallback`.

The subtypes of `AbstractZonotope` (including abstract interfaces):

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractZonotope)
4-element Vector{Any}:
 AbstractHyperrectangle
 HParallelotope
 LineSegment
 Zonotope
```
