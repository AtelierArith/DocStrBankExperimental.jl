```
raviartthomas(mesh, cellpairs::Array{Int,2})
```

Constructs the RT basis on the input `mesh`. The i-th RT basis function will     represent a current distribution flowing from cell `cellpairs[1,i]` to     `cellpairs[2,i]` on the mesh.

Returns an object of type `RTBasis`, which comprises both the mesh and pairs of     Shape objects which corresponds to the cell pairs, containing the necsessary     coefficients and indices to compute the exact basis functions when required     by the solver.
