```
diffSVD(φ::Matrix{Float64}, μ::Vector{Float64}, X::Matrix{Float64})

UNTESTED 

linear operator components and singular value decomposition
as in algorithm that starts on line 15 of supplement of 10.1073/pnas.1118984109

Arguments
=================
- φ: diffusion eigenfunctions of size s × L 
- μ: vector of size s that are the wieghts from the normW function
- X: original data (after embedding), where dim 2 is the embedding space of size N
```
