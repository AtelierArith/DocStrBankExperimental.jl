```
curvature(b::Blob, n::Int)
```

Compute an array that measures the angular difference between the pixel n before and n after then current one for each point on the perimeter of the blob. Negative indicates convex and positive indicates concave with large positive values indicating a sharp concave angle.
