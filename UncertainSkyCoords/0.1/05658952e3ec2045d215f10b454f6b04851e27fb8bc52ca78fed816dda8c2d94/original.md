```
UEllipseAAFlat(; ulon, ulat, lat::Number)
UEllipseAAFlat(; uloncoslat, ulat)
```

Uncertainty in the shape of an axis-aligned ellipse with separate uncertainties in the `lon` and `lat` directions.

Assumes a locally-flat sky with orthogonal `lon` and `lat` directions. This is a great approximation for small sky regions, but be careful when using it for large regions or close (comparable to the uncertainty) to the poles.

The `lat` value is necessary to convert `ulon` to `uloncoslat` so that all downstrem calculations happen in the same tangent plane coordinate system.
