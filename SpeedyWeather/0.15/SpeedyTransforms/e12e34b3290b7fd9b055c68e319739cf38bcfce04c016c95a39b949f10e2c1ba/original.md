```julia
curl(
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Any

```

Curl (∇×) of two vector components `u, v` of size (n+1)xn, the last row will be set to zero in the returned `LowerTriangularMatrix`. This function requires both `u, v` to be transforms of fields that are scaled with `1/cos(lat)`. Acts on the unit sphere, i.e. it omits 1/radius scaling unless `radius` keyword argument is provided. An example usage is therefore

```
RingGrids.scale_coslat⁻¹!(u_grid)
RingGrids.scale_coslat⁻¹!(v_grid)
u = transform(u_grid)
v = transform(v_grid)
vor = curl(u, v, radius=6.371e6)
vor_grid = transform(div)
```
