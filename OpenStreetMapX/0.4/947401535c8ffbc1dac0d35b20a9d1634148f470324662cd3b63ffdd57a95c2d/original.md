```
LLA(nodes::Dict{Int,ECEF}, datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

Converts a dictionary of `ECEF` `nodes` into a dictionary of `LLA` values.

**Arguments**

  * `nodes::Dict{Int,ECEF}` : Dictionary of ECEF nodes.
  * `datum::OpenStreetMapX.Ellipsoid` : type of ellipsoid used.
