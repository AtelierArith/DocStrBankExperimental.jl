```
connectivity(faces, cells, op=sign)
```

Create a sparse matrix `D` of size `numcells(cells)` by `numcells(faces)` that contiains the connectivity info of the mesh. In particular `D[m,k]` is `op(r)` where `r` is the local index of face `k` in cell `m`. The sign of `r` is positive or negative depending on the relative orientation of face `k` in cell `m`.

For `op=sign`, the matrix returned is the classic connectivity matrix, i.e. the graph version of the exterior derivative.
