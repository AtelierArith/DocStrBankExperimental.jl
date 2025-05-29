`CudaOffloadFactorization()`

An offloading technique used to GPU-accelerate CPU-based computations. Requires a sufficiently large `A` to overcome the data transfer costs.

!!! note
    Using this solver requires adding the package CUDA.jl, i.e. `using CUDA`

