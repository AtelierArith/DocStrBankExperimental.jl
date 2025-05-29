```
ECEF(nodes::Dict{Int,LLA}, datum::OpenStreetMapX.Ellipsoid = OpenStreetMapX.WGS84)
```

Converts a dictionary of `LLA` `nodes` into a dictionary of `ECEF` values. Uses a reference point `lla_ref` for linearization.

**Arguments**

  * `nodes::Dict{Int,LLA}` : Dictionary of LLA nodes.
  * `datum::OpenStreetMapX.Ellipsoid` : type of ellipsoid used.
