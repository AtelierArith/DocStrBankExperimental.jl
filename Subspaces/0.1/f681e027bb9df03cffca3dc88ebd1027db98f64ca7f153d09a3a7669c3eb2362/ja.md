```julia
random_hermitian_subspace(
    T::Type,
    d::Int64,
    n::Int64
) -> Subspaces.Subspace
random_hermitian_subspace(
    T::Type,
    d::Int64,
    n::Int64,
    tol
) -> Subspaces.Subspace

```

基底体 `T` の `n × n` 行列の次元 `d` のランダム部分空間で、`x ∈ S => x' ∈ S` を満たします。

```jldoctest
julia> S = random_hermitian_subspace(ComplexF64, 2, 3)
Subspace{Complex{Float64}} size (3, 3) dim 2

julia> S == S'
true
```
