```julia
full_subspace(T::Type, siz::Tuple) -> Subspaces.Subspace

```

Create an full subspace of dimension-`siz` vector space, on base field `T`.

```jldoctest
julia> S = full_subspace(ComplexF64, (3, 4))
Subspace{Complex{Float64}} size (3, 4) dim 12
```
