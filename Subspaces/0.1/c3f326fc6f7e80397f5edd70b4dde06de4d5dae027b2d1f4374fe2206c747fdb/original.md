```julia
empty_subspace(T::Type, siz::Tuple) -> Subspaces.Subspace
empty_subspace(
    T::Type,
    siz::Tuple,
    tol
) -> Subspaces.Subspace

```

Create an empty subspace of dimension-`siz` vector space, on base field `T`.

```jldoctest
julia> S = empty_subspace(ComplexF64, (3, 4))
Subspace{Complex{Float64}} size (3, 4) dim 0
```
