```julia
empty_subspace(T::Type, siz::Tuple) -> Subspaces.Subspace
empty_subspace(
    T::Type,
    siz::Tuple,
    tol
) -> Subspaces.Subspace

```

次元`siz`のベクトル空間の空の部分空間を、基底体`T`の上に作成します。

```jldoctest
julia> S = empty_subspace(ComplexF64, (3, 4))
Subspace{Complex{Float64}} size (3, 4) dim 0
```
