```
separation(c1::AbstractSkyCoords, c2::AbstractSkyCoords) -> distance
```

Return angular separation between two sky coordinates, in radians.

The angular separation is calculated using the [Vincenty formula](http://en.wikipedia.org/wiki/Great-circle_distance), which is slightly more complex and computationally expensive than some alternatives, but is stable at at all distances, including the poles and antipodes.
