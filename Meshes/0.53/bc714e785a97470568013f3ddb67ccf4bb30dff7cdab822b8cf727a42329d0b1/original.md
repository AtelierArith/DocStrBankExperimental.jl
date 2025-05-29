```
RegularSampling(n1, n2, ..., np)
```

Generate samples regularly using `n1` points along the first parametric dimension, `n2` points along the second parametric dimension, ..., `np` points along the last parametric dimension.

## Examples

Sample sphere regularly with 360 longitudes and 180 latitudes:

```julia
sample(Sphere((0,0,0), 1), RegularSampling(360, 180))
```
