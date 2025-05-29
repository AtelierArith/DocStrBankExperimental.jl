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

次元-`d` のランダム部分空間は、次元-`siz` のベクトル空間で、基底体は `T` です。

```jldoctest
julia> S = random_subspace(ComplexF64, 2, (3, 4))
Subspace{Complex{Float64}} size (3, 4) dim 2
```
