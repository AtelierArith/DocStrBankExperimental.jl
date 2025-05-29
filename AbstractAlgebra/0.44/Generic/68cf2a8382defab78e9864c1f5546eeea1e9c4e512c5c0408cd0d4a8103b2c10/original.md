```
character(lambda::Partition)
```

Return the $\lambda$-th irreducible character of permutation group on `sum(lambda)` symbols. The returned character function is of the following signature:

> `chi(p::Perm[, check::Bool=true]) -> BigInt`


The function checks (if `p` belongs to the appropriate group) can be switched off by calling `chi(p, false)`. The values computed by $\chi$ are cached in look-up table.

The computation follows the Murnaghan-Nakayama formula: $\chi_\lambda(\sigma) = \sum_{\text{rimhook }\xi\subset \lambda}(-1)^{ll(\lambda\backslash\xi)} \chi_{\lambda \backslash\xi}(\tilde\sigma)$ where $\lambda\backslash\xi$ denotes the skew diagram of $\lambda$ with $\xi$ removed, $ll$ denotes the leg-length (i.e. number of rows - 1) and $\tilde\sigma$ is permutation obtained from $\sigma$ by the removal of the longest cycle.

For more details see e.g. Chapter 2.8 of *Group Theory and Physics* by S.Sternberg.

# Examples

```jldoctest
julia> G = SymmetricGroup(4)
Full symmetric group over 4 elements

julia> chi = character(Partition([3,1])); # character of the regular representation


julia> chi(one(G))
3

julia> chi(perm"(1,3)(2,4)")
-1
```
