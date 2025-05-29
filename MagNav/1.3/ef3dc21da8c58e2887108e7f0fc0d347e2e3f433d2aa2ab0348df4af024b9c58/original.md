```
map_interpolate(map_map::AbstractArray{T},
                map_xx::AbstractVector{T},
                map_yy::AbstractVector{T},
                type::Symbol = :cubic,
                map_alt::AbstractVector{T} = T[0]) where T
```

Create map interpolation function, equivalent of griddedInterpolant in MATLAB.

**Arguments:**

  * `map_map`: `ny` x `nx` (x `nz`) 2D or 3D gridded map data
  * `map_xx`:  `nx` map x-direction (longitude) coordinates
  * `map_yy`:  `ny` map y-direction (latitude)  coordinates
  * `type`:    (optional) type of interpolation {:linear,:quad,:cubic}
  * `map_alt`: (optional) map altitude levels

**Returns:**

  * `itp_map`: map interpolation function (`f(yy,xx)` or (`f(yy,xx,alt)`)
