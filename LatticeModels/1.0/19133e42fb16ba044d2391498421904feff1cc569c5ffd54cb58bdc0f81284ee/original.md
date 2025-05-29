```
PointFlux(flux, [point; gauge])
```

Construct a `PointFlux` object with given flux and point.

The optional `gauge` argument can be used to specify the gauge of the field. Possible values are `:axial` ($A(r) = B \times \frac{r}{|r|}$) and `:singular` (the the phase changes if the particle passes below the point). The default is `:axial`.
