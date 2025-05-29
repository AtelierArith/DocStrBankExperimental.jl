```julia
isBandGapped(H::Hamiltonian ; tol::Float64 = 1e-3) --> BitMatrix
```

Returns a matrix of booleans marked as `true` if the band corresponding to the row and column of the matrix are gapped (greater than the tolerance), and false otherwise. 
