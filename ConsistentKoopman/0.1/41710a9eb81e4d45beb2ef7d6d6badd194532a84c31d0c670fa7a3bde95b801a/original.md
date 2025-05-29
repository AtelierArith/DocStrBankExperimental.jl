```
koopmanop(shifts::Vector{Int64}, φ::Matrix{Float64}, w::Vector{Float64})

compute approximation of Koopman operator using a shift matrix on a basis of observables (φ)

Arguments
=================
- shifts: a vector of shifts to apply, if only one give as a vector, i.e. [3] because I am very lazy 
- φ: diffusion eigenfunctions of size s × L 
- w: inner product weight array of size s × 1

tested on Sept 14, 2023
```
