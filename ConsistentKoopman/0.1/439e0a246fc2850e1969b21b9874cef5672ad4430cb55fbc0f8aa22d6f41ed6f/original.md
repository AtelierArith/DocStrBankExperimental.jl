```
projectDiffEigs(φ::Matrix{Float64}, μ::Vector{Float64}, X::Matrix{Float64}, q::Integer = 1)

UNTESTED

computes projection of diffusion eigenvalues to physical space,
from 10.1073/pnas.1118984109

Arguments
=================
- φ: takes diffusion eigenfunctions of size s × L 
- μ: vector of size s that are the wieghts from the normW function
- X: original data (after embedding), where dim 2 is the embedding space of size N

Keyword arguments
=================
- q: number of delays (no delays means q = 1)
```
