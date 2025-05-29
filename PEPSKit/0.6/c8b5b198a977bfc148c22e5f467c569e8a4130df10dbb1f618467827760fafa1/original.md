```julia
struct LocalOperator{T<:Tuple, S}
```

A sum of local operators acting on a lattice. The lattice is stored as a matrix of vector spaces, and the terms are stored as a tuple of pairs of indices and operators.

## Fields

  * `lattice::Matrix{S}`: The lattice on which the operator acts.
  * `terms::T`: The terms of the operator, stored as a tuple of pairs of indices and operators.

## Constructors

```
LocalOperator(lattice::Matrix{S}, terms::Pair...)
LocalOperator{T,S}(lattice::Matrix{S}, terms::T) where {T,S}
```

## Examples

```julia
lattice = fill(ℂ^2, 1, 1) # single-site unitcell
O1 = LocalOperator(lattice, ((1, 1),) => σx, ((1, 1), (1, 2)) => σx ⊗ σx, ((1, 1), (2, 1)) => σx ⊗ σx)
```
