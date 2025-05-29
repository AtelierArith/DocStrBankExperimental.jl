```
neighbors(p::VoronoiPolygon, grid::VoronoiGrid)
```

Create an iterator through all Voronoi polygons that neighbor the polygon `p`.  Use it in a for loop to iterate through all triplets `(q,e,y)` where 

  * `q` = the neighboring polygon
  * `e` = the edge connecting `p` and `q`
  * `y` = the position of `q` as a neighbor of `p` (equivalent to `q.x` for non-periodic grids)
