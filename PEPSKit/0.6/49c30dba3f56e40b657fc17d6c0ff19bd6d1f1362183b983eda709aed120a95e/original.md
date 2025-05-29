```
simpleupdate(peps::InfiniteWeightPEPS, H::LocalOperator, alg::SimpleUpdate;
             bipartite::Bool=false, check_interval::Int=500)
```

Perform simple update with nearest neighbor Hamiltonian `H`, where the evolution information is printed every `check_interval` steps. 

If `bipartite == true` (for square lattice), a unit cell size of `(2, 2)` is assumed,  as well as tensors and x/y weights which are the same across the diagonals, i.e. at `(row, col)` and `(row+1, col+1)`.
