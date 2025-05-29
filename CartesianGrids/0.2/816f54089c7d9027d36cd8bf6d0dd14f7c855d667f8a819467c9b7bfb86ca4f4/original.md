```
grid_interpolate!(v::Nodes{Dual/Primal},q::Nodes{Primal/Dual})
```

Interpolate the primal (resp. dual) node data `q` to the edges of the dual (resp. primal) nodes, and return the result in `v`.
