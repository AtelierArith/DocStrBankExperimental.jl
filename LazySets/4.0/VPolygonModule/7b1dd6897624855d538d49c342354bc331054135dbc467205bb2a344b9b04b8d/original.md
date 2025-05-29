# Extended help

```
σ(d::AbstractVector, P::VPolygon)
```

### Output

If the direction has norm zero, the first vertex is returned.

### Algorithm

This implementation uses a binary search algorithm when the polygon has more than 10 vertices and a brute-force search when it has 10 or fewer vertices. The brute-force search compares the projection of each vector along the given direction and runs in $O(n)$ where $n$ is the number of vertices. The binary search runs in $O(log n)$ and we follow [this implementation](http://geomalgorithms.com/a14-_extreme_pts.html#polyMax_2D()) based on an algorithm described in [ORourke98](@citet).
