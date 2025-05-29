```julia
full_subspace(T::Type, siz::Tuple) -> Subspaces.Subspace

```

次元`siz`のベクトル空間の完全部分空間を、基底体`T`の上に作成します。

```jldoctest
julia> S = full_subspace(ComplexF64, (3, 4))
Subspace{Complex{Float64}} size (3, 4) dim 12
```
