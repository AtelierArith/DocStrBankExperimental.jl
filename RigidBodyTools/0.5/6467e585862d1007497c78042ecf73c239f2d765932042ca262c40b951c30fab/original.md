```
Rectangle(a,b,n) <: Body
```

Construct a rectangular body with x̃ side half-length `a` and ỹ side half-length `b`, with approximately `n` points distributed along the perimeter. The centroid of the rectangle is placed at the origin (so that the lower left corner is at (-a,-b)).

Points are not placed at the corners, but rather, are shifted by half a segment. This ensures that all normals are perpendicular to the sides.
