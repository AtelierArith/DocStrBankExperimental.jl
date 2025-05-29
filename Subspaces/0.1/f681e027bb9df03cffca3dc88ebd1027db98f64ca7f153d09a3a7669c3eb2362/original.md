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

Random dimension-`d` subspace of `n × n` matrices on base field `T`, satisfying `x ∈ S => x' ∈ S`.

```jldoctest
julia> S = random_hermitian_subspace(ComplexF64, 2, 3)
Subspace{Complex{Float64}} size (3, 3) dim 2

julia> S == S'
true
```
