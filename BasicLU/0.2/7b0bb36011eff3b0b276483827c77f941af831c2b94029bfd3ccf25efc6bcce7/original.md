```
L, U, p, q = getfactors(F::LUFactor) -> L::SparseMatrixCSC{Float64, Int64},
                                              U::SparseMatrixCSC{Float64, Int64},
                                              p::Vector{Int64},
                                              q::Vector{Int64}
```

Extract LU factors after fresh factorization. `L` is unit lower triangular, `U` is upper triangular and `p` and `q` are permutation vectors such that (ignoring round-off errors) `B[p,q] = L * U` when matrix `B` was factorizied.
