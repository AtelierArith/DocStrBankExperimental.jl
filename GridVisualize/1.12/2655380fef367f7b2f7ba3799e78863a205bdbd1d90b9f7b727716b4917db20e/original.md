```
 function quiverdata(rastercoord,
                     rasterflux;
                     vscale = 1.0,
                     vnormalize = true,
                     vconstant = false)
```

Extract  nonzero fluxes for quiver plots from rastergrid obtained by [`vectorsample`](@ref).

Returns qc, qv -  `d x nquiver` matrices.

If vnormalize is true, the vector field is normalized to vscale*min(spacing), otherwise, it is scaled by vscale Result data are meant to  be ready for being passed to calls to `quiver` with various plotting backends.
