```
MvLocationScale(location, scale, dist)
```

The location scale variational family broadly represents various variational families using `location` and `scale` variational parameters.

It generally represents any distribution for which the sampling path can be represented as follows:

```julia
  d = length(location)
  u = rand(dist, d)
  z = scale*u + location
```
