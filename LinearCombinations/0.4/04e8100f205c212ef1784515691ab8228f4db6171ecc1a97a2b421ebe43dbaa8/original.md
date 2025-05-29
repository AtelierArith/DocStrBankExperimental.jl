```
TensorBasis{T,N} <: AbstractBasis{T,N}

TensorBasis(bases...)
```

Construct a `TensorBasis` out of the given bases. The elements of the `TensorBasis` are of type `Tensor`, where the `i`-th tensor component is from the `i`-th basis.

See also [`AbstractBasis`](@ref), [`Basis`](@ref).

# Examples

```jldoctest
julia> b1, b2 = Basis('a':'c'), Basis(["x", "y", "z"])
(Basis('a':1:'c'), Basis(["x", "y", "z"]))

julia> b3 = TensorBasis(b1, b2)
TensorBasis(Basis('a':1:'c'), Basis(["x", "y", "z"]))

julia> length(b3)
9

julia> toindex(b3, Tensor('b', "z"))
CartesianIndex(2, 3)

julia> b4 = TensorBasis(b3, b1)
TensorBasis(TensorBasis(Basis('a':1:'c'), Basis(["x", "y", "z"])), Basis('a':1:'c'))

julia> ndims(b4)
3

julia> x = first(b4)
('a'⊗"x")⊗'a'

julia> toindex(b4, x)
CartesianIndex(1, 1, 1)

julia> b0 = TensorBasis(); length(b0), Tensor() in b0
(1, true)
```
