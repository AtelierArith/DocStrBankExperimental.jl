```
amd(A)
amd(A, meta)
```

Given a sparse matrix `A` and an `Amd` structure `meta`, `p = amd(A, meta)` computes the approximate minimum degree ordering of `A + Aᵀ`. The ordering is represented as a permutation vector `p`. Factorizations of `A[p,p]` tend to be sparser than those of `A`.

The matrix `A` must be square and the sparsity pattern of `A + Aᵀ` is implicit. Thus it is convenient to represent symmetric or hermitian matrices using one triangle only. The diagonal of `A` may be present but will be ignored.

The ordering may be influenced by changing `meta.control[AMD_DENSE]` and `meta.control[AMD_AGGRESSIVE]`.

Statistics on the ordering appear in `meta.info`.
