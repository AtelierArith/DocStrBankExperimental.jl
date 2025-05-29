```
allocate_on(M::AbstractManifold, [T:::Type])
allocate_on(M::AbstractManifold, F::FiberType, [T:::Type])
```

Allocate a new point on manifold `M` with optional type given by `T`. Note that `T` is not number element type as in [`allocate`](@ref) but rather the type of the entire point to be returned.

If `F` is provided, then an element of the corresponding fiber is allocated, assuming it is independent of the base point.

To allocate a tangent vector, use ``

# Example

```julia-repl
julia> using ManifoldsBase

julia> M = ManifoldsBase.DefaultManifold(4)
DefaultManifold(4; field = ℝ)

julia> allocate_on(M)
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

julia> allocate_on(M, Array{Float64})
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

julia> allocate_on(M, TangentSpaceType())
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

julia> allocate_on(M, TangentSpaceType(), Array{Float64})
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

```
