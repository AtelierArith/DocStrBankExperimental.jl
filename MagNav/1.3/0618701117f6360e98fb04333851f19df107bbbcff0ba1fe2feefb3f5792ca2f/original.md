```
map_interpolate(mapS::Union{MapS,MapSd,MapS3D}, type::Symbol = :cubic;
                return_vert_deriv::Bool = false)
```

Create map interpolation function, equivalent of griddedInterpolant in MATLAB. Optionally return vertical derivative map interpolation function, which is calculated using finite differences between map and 1 m upward continued map.

**Arguments:**

  * `mapS`:              `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `type`:              (optional) type of interpolation {:linear,:quad,:cubic}
  * `return_vert_deriv`: (optional) if true, also return `der_map`

**Returns:**

  * `itp_map`: map interpolation function (`f(yy,xx)` or (`f(yy,xx,alt)`)
  * `der_map`: if `return_vert_deriv = true`, vertical derivative map interpolation function (`f(yy,xx)` or (`f(yy,xx,alt)`)
