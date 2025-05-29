```julia
tobasis(
    S::Subspaces.Subspace{<:Number, N},
    x::AbstractArray{<:Number, N}
) -> Any

```

`x`の基底成分を`S.basis`の基底で返します。

関連: [`frombasis`](@ref).

```jldoctest
julia> S = random_subspace(ComplexF64, 2, 10)
Subspace{Complex{Float64}} size (10,) dim 2

julia> x = randn(10);

julia> size(tobasis(S, x))
(2,)

julia> norm( frombasis(S, tobasis(S, x)) - projection(S, x) ) < 1e-8
true
```
