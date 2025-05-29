```
eigen(A::ITensor[, Linds, Rinds]; <keyword arguments>)
```

Eigendecomposition of an ITensor `A`, computed by treating the "left indices" `Linds` provided collectively as a row index, and remaining "right indices" `Rinds` as a column index (matricization of a tensor).

If no indices are provided, pairs of primed and unprimed indices are searched for, with `Linds` taken to be the primed indices and `Rinds` taken to be the unprimed indices.

The return arguments are the eigenvalues `D` and eigenvectors `U` as tensors, such that `A * U ∼ U * D` (more precisely they are approximately equal up to proper replacements of indices, see the example for details).

Whether or not `eigen` performs a trunction depends on the keyword arguments provided. Note that truncation is only well defined for positive semidefinite matrices.

# Arguments

```
- `maxdim::Int`: the maximum number of singular values to keep.
- `mindim::Int`: the minimum number of singular values to keep.
- `cutoff::Float64`: set the desired truncation error of the eigenvalues,
   by default defined as the sum of the squares of the smallest eigenvalues.
   For now truncation is only well defined for positive semi-definite
   eigenspectra.
- `ishermitian::Bool = false`: specify if the matrix is Hermitian, in which
   case a specialized diagonalization routine will be used and it is
   guaranteed that real eigenvalues will be returned.
- `plev::Int = 0`: set the prime level of the Indices of `D`. Default prime
   levels are subject to change.
- `leftplev::Int = plev`: set the prime level of the Index unique to `D`.
   Default prime levels are subject to change.
- `rightplev::Int = leftplev+1`: set the prime level of the Index shared
   by `D` and `U`. Default tags are subject to change.
- `tags::String = "Link,eigen"`: set the tags of the Indices of `D`.
   Default tags are subject to change.
- `lefttags::String = tags`: set the tags of the Index unique to `D`.
   Default tags are subject to change.
- `righttags::String = tags`: set the tags of the Index shared by `D` and `U`.
   Default tags are subject to change.
- `use_absolute_cutoff::Bool = false`: set if all probability weights below
   the `cutoff` value should be discarded, rather than the sum of discarded
   weights.
- `use_relative_cutoff::Bool = true`: set if the singular values should
   be normalized for the sake of truncation.
```

# Examples

```julia
i, j, k, l = Index(2, "i"), Index(2, "j"), Index(2, "k"), Index(2, "l")
A = random_itensor(i, j, k, l)
Linds = (i, k)
Rinds = (j, l)
D, U = eigen(A, Linds, Rinds)
dl, dr = uniqueind(D, U), commonind(D, U)
Ul = replaceinds(U, (Rinds..., dr) => (Linds..., dl))
A * U ≈ Ul * D # true
```

See also: [`svd`](@ref), [`factorize`](@ref)
