```
InfiniteMPOHamiltonian(Ws::Vector{<:Matrix})
```

Create a `InfiniteMPOHamiltonian` from a vector of matrices, such that `Ws[i][j, k]` represents the the operator at site `i`, left level `j` and right level `k`. Here, the entries can be either `MPOTensor`, `Missing` or `Number`.
