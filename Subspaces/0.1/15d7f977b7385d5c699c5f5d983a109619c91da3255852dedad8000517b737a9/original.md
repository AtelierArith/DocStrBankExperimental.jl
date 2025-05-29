```julia
each_basis_element(
    S::Subspaces.Subspace
) -> Slices{P, _A, AX, T, 1} where {P<:Array, _A, AX<:Tuple{Any}, T}

```

Create a generator that iterates over orthonormal basis vectors of a subspace.
