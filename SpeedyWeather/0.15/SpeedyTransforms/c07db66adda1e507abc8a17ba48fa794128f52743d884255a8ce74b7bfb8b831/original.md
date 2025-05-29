```julia
divergence(
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Divergence (∇⋅) of two vector components `u, v` which need to have size (n+1)xn, the last row will be set to zero in the returned `LowerTriangularMatrix`. This function requires both `u, v` to be transforms of fields that are scaled with `1/cos(lat)`. Acts on the unit sphere, i.e. it omits 1/radius scaling unless `radius` keyword argument is provided. An example usage is therefore

```
RingGrids.scale_coslat⁻¹!(u_grid)
RingGrids.scale_coslat⁻¹!(v_grid)
u = transform(u_grid, one_more_degree=true)
v = transform(v_grid, one_more_degree=true)
div = divergence(u, v, radius = 6.371e6)
div_grid = transform(div)
```
