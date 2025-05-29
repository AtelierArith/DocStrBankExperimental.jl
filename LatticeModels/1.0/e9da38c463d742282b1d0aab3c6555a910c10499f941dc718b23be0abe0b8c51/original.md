```
PointFluxes([fluxes, points; offset=(0, 0), gauge=:axial])
```

Construct a `PointFluxes` object with given fluxes and points.

The optional `gauge` argument can be used to specify the gauge of the field.

## Arguments

  * `fluxes`: A vector of flux values. Also can be a single value, in which case it will be broadcasted to all points.
  * `points`: A vector of points or a `AbstractLattice` object. In the latter case the sites will be interpreted as points.

If both arguments are omitted, an empty field is created. You can add fluxes to it later using `push!` or `append!`.

## Keyword arguments

  * `offset`: An offset to add to the points, default is `(0, 0)`. Valid only if `points` is a `AbstractLattice`, otherwise an error is thrown.
  * `gauge`: The gauge of the field. Possible values are `:axial` and `:singular`. The default is `:axial`.
