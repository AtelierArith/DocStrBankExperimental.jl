resolventop_power(φ::Matrix{Float64}, w::Vector{Float64}, Tf::Int64, dt::Float64, z::Float64; batchN = 1)

```
compute approximation of Koopman operator using a shift matrix on a basis of observables (φ)

Arguments
=================
- φ: diffusion eigenfunctions of size s × L 
- w: inner product weight array of size s × 1
- Tf: final time to integrate to
- dt: data spacing
- z: real number to evaluate resolvent at

Keyword arguments
=================
- batchN: number of batches in which to run quadrature

tested on Sept 14, 2023
```
