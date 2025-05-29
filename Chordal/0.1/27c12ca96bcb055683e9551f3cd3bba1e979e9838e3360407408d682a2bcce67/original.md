```
get_chordal_extension(sp_pattern::SparseMatrixCSC; perm="amd", verbose=false)
```

Returns `p, ip, L`, where `L` is a lower-triangular matrix representing the chordal extension of the undirected graph `sp_pattern` after fill-reducing permutation `p` (with inverse permutation `ip`).

Options for perm include 	- `"nothing"` (no permutation) 	- `amd` (approximate minimum degree) 	- `metis` (uses [METIS](http://glaros.dtc.umn.edu/gkhome/metis/metis/overview)) 	- `cuthill-mckee` (Cuthill-McKee bandwidth reducing algorithm)
