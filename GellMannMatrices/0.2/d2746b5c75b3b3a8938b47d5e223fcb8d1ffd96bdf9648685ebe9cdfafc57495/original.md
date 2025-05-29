```
gellmann([T::Type{<:AbstractMatrix} = Matrix{ComplexF64},] d::Integer;
         skip_identity = true, normalize = false)
```

Return the generalized Gell-Mann matrices in `d` dimensions as a vector of matrices of type `T`.

`T` can be any mutable `AbstractMatrix`, including `SparseMatrixCSC`, with `eltype(T)` equal to any complex floating point type.

## Keyword arguments

  * `skip_identity` (default, `true`): if `false`, the identity matrix of dimension `d` is included as the last element of the returned vector.
  * `normalize` (default, `false`): if `true`, matrices are normalized in a manner that ensures the orthonormality relation `tr(Mᵢ'*Mⱼ) = 2δᵢⱼ`; if `false`, a choice of matrix elements favoring simplicity is made (i.e., integer elements).

## Examples

Compute the Pauli matrices $σ_i$ (`d=2`) and Gell-Mann matrices $Λ_i$ (`d=3`):

```jl
julia> σᵢ = gellmann(2)
julia> Λᵢ = gellmann(3)
```
