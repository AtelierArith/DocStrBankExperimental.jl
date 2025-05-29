```
spaceagg(f, A::ClimArray, W = nothing)
```

Aggregate `A` using function `f` (e.g. `mean, std`) over all available space (i.e. longitude and latitude) of `A`, weighting every part of `A` by its spatial area.

`W` can be extra weights, to weight each spatial point with. `W` can either be a `ClimArray` with same spatial information as `A`, or having exactly same dimensions as `A`.
