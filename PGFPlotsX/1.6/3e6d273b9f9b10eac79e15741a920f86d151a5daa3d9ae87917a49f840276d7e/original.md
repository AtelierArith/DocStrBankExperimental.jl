```julia
Coordinates(x, y, z; meta)

```

Construct coordinates from a matrix of values and edge vectors, such that `z[i,j]` corresponds to `x[i]` and `y[j]`. Empty scanlines are inserted, consistently with the `mesh/ordering=x varies` option of PGFPlots (the default).

```julia
x = range(0; stop = 1, length = 10)
y = range(-1; stop = 2, length = 13)
z = sin.(x) + cos.(y')
Coordinates(x, y, z)
```
