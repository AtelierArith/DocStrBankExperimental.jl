```
HamiltonianKGrid(hami::TBHamiltonian{T}, nk, H_function_k::Function = x -> nothing) where T
HamiltonianKGrid(hami::TBHamiltonian{T}, k_grid, H_function_k::Function = x -> nothing) where T
```

Takes a k grid, calculates Hk for each of them and diagonalizes. Only the eigenvectors and eigenvalues of Hk are stored, the `H_function_k` function is called on the intermediate Hk. 
