```
D = randinpolygon(Din; density=0.1, np::Int=0)
```

Generate random samples inside polygons. The method used here is that of poin-in-polygon. That is, we generate random points inside a rectangular BoundingBox of each polygon and retain those inside the polygon. For geographical polygons we generate random angles but do NOT connect the polygon sides with great circles, so solution is not really geographic but the error is rather small if the polygon vertices are close to each other.

  * `Din`: The input polygons. It can be a $GMTdaset$, a vector of them or a Mx2 matrix with the polygon vertices.
  * `density`: the average density of the randomly generated points. For the Cartesian case this is a percentage that can be expressed in the ]0 1] or ]0 100] interval. For example, the default `density=0.1` means that points are created more or less at 1/10th of polygon's side. For geographical polygons (identified by the `proj` fields of the `GMTdataset`) the `density` means number of points per degree. The default of 20 represents a point scattering of about 1 every 5 km.
  * `np`: The approximate number of points in each polygon. Note that this option overrides `density` and is not an exact requirement. That is `np=10` might return 9 or 11 or other number of points.

### Returns

A GMTdatset if only one polygon was passed or a Vector{GMTaset} otherwise.
