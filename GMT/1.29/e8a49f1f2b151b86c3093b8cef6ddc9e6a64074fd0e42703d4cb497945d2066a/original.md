```
Dtiles, zoomL = quadbounds(quadtree; geog=true, quadkey=['0' '1'; '2' '3'])
```

Compute the coordinates of the `quadtree` quadtree. Either a single quadtree string or an array of quadtree strings.

  * `quadtree`: Either a single quadtree string or a `Matrix{String}` of quadtree strings. This is the quadtree string or array of strings to compute coordinates for and is obtained from a call to the `mosaic` using the `quadonly` option (see example below).
  * `quadkey=['0' '1'; '2' '3']`: The quadkey for the quadtree.

### Returns

  * `Dtiles`: A GMTdataset vector with the corner coordinates of each tile.
  * `zoomL`: Zoom level of the tiles.

### Example

```jldoctest
  quadtree = mosaic([-10. -8],[37. 39.], zoom=8, quadonly=1)[1];
  D = quadbounds(quadtree)[1];
  viz(D)
```
