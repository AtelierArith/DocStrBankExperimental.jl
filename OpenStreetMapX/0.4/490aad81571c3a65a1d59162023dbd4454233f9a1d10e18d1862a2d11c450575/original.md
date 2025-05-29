```
ECEF(nodes::Dict{Int,ENU},lla_ref::LLA , datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

Converts a dictionary of `ENU` `nodes` into a dictionary of `ECEF` values. Uses a reference point `lla_ref` for linearization.

**Arguments**

  * `nodes::Dict{Int,ENU},` : Dictionary of ENU nodes.
  * `lla_ref::LLA` : Reference point for linarization
  * `datum::OpenStreetMapX.Ellipsoid` : type of ellipsoid used.
