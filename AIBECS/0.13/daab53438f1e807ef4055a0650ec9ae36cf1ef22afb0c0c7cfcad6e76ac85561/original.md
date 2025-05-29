```
transportoperator(grd, w)
```

Returns the transportoperator for the given settling velocity `w`.

The settling velocity can be provided as either a scalar (e.g., `w = 100.0` in units of meters per second) or as a function of depth (e.g., `w(z) = 2z + 1`).

# Examples

Create the particle flux divergence with settling velocity of 100m/s

```julia-repl
julia> T = transportoperator(grd, 100.0)
```

Or with settling velocity function w(z) = 2z + 1

```julia-repl
julia> T = transportoperator(grd, z -> 2z + 1)
```

By default, the seafloor flux is set to zero, so that all the particles that reach it are remineralized there. You can let particles go through by setting `fsedremin=0.0`, via, e.g.,

```julia-repl
julia> T = transportoperator(grd, z -> 2z + 1; fsedremin=0.0)
```

For finer control and advanced use, see the particle-flux divergence operator function, `PFDO`.
