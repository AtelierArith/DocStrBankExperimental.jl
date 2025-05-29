```
get_computational_nt(srcGeometry, recGeoemtry, model; dt=nothing)
```

Estimate the number of computational time steps. Required for calculating the dimensions
of the matrix-free linear modeling operators. `srcGeometry` and `recGeometry` are source
and receiver geometries of type `Geometry` and `model` is the model structure of type 
`Model`.
