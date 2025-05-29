`UMFPACKFactorization(;reuse_symbolic=true, check_pattern=true)`

A fast sparse multithreaded LU-factorization which specializes on sparsity patterns with “more structure”.

!!! note
    By default, the SparseArrays.jl are implemented for efficiency by caching the symbolic factorization. I.e., if `set_A` is used, it is expected that the new `A` has the same sparsity pattern as the previous `A`. If this algorithm is to be used in a context where that assumption does not hold, set `reuse_symbolic=false`.

