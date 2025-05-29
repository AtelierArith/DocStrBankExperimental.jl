```julia
frombasis(
    S::Subspaces.Subspace,
    x::AbstractVector{<:Number}
) -> Any

```

Returns a vector from the given basis components in the basis `S.basis`.

See also: [`tobasis`](@ref).

```jldoctest
julia> S = random_subspace(ComplexF64, 2, 10)
Subspace{Complex{Float64}} size (10,) dim 2

julia> x = randn(2);

julia> size(frombasis(S, x))
(10,)

julia> norm( tobasis(S, frombasis(S, x)) - x ) < 1e-8
true
```
