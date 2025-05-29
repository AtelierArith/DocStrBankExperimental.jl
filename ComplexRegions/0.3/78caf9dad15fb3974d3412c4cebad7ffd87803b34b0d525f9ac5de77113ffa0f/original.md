```
truncate(P::Union{CircularPolygon,Polygon})
```

Apply `truncate` to `P` using a circle that is centered at the centroid of its finite vertices, and a radius twice the maximum from the centroid to the finite vertices.
