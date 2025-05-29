```
PauliVec
```

A constant that holds the eigenvectors of the Pauli matrices. Indices 1, 2 and 3 corresponds to the eigenvectors of $σ_x$, $σ_y$ and $σ_z$.

# Examples

```julia-repl
julia> σx*PauliVec[1][1] == PauliVec[1][1]
true
```
