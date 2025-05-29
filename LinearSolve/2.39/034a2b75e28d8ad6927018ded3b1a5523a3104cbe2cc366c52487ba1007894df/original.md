`RFLUFactorization()`

A fast pure Julia LU-factorization implementation using RecursiveFactorization.jl. This is by far the fastest LU-factorization implementation, usually outperforming OpenBLAS and MKL for smaller matrices (<500x500), but currently optimized only for Base `Array` with `Float32` or `Float64`. Additional optimization for complex matrices is in the works.
