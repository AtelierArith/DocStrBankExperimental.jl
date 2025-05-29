```
FiniteMPOHamiltonian(Ws::Vector{<:Matrix})
```

Create a `FiniteMPOHamiltonian` from a vector of matrices, such that `Ws[i][j, k]` represents the operator at site `i`, left level `j` and right level `k`. Here, the entries can be either `MPOTensor`, `Missing` or `Number`.
