```julia
random_subspace(
    T::Type,
    d::Int64,
    siz
) -> Subspaces.Subspace
random_subspace(
    T::Type,
    d::Int64,
    siz,
    tol
) -> Subspaces.Subspace

```

Random dimension-`d` subspace of dimension-`siz` vector space, on base field `T`.

```jldoctest
julia> S = random_subspace(ComplexF64, 2, (3, 4))
Subspace{Complex{Float64}} size (3, 4) dim 2
```
