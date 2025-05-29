```
ThinGratingInterface{T} <: OpticalInterface{T}
```

Interface representing an idealized thin grating. `period` is in microns, `vector` should lie in the plane of the surface. Transmission and reflectance can be specified for an arbitrary number of orders up to 10, selected using the `maxorder` and `minorder` parameters. If `nothing` then `reflectance` is assumed to be **0** and `transmission` is assumed to be **1**.

```julia
ThinGratingInterface(vector, period, insidematerial, outsidematerial; maxorder = 1, minorder = -1, reflectance = nothing, transmission = nothing)
```
