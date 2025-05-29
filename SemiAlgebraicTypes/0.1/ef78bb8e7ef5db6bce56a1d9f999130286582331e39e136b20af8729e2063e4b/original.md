```
remove_doublon!(m::Mesh{Float64}, eps::Float64=1.e-3)
```

Replace duplicate points which are within distance eps by a single point.

The default value for eps is 1.e-3.

Warning: The normals are not taken into account.
