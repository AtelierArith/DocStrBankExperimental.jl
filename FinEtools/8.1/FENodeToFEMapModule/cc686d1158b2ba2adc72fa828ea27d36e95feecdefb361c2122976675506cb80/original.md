```
FENodeToFEMap(conn::Vector{NTuple{N, IT}}, nmax::FInt) where {N, IT<:Integer}
```

Map from finite element nodes to the finite elements connecting them.

  * `conns` = connectivities as a vector of tuples
  * `nmax` = largest possible node number

Example:

```
m = FENodeToFEMap(fes.conn, count(fens))
```
