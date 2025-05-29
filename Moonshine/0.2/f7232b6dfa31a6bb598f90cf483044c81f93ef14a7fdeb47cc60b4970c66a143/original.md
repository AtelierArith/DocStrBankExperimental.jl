```
cbasis!(vec, arg, v, lk; estack, edgesid, vqueue, visited)
cbasis(arg, v, lk; estack, edgesid, vqueue, visited)
cbasis!(mat, arg; edgesid)
cbasis(arg; edgesid)
```

Compute the basis vector associated with recombination vertex `v`. If `v` is not specified, return a matrix containing all basis vectors.
