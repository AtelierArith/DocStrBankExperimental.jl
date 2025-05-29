```
ENU(nodes::Dict{Int,T}, lla_ref::LLA,datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84) where T<:Union{LLA,ECEF}
```

Converts a dictionary of `LLA` and `ECEF` `nodes` into a dictionary of `ENU` values. Uses a reference point `lla_ref` for linearization.

**Arguments**

  * `nodes::Dict{Int,T}` : Dictionary of LLA or ECEF nodes.
  * `lla_ref::LLA` : Reference point for linarization
  * `datum::OpenStreetMapX.Ellipsoid` : type of ellipsoid used.
