```
convex_hull(points, alg=GiftWrappingAlg())
```

Determine the indices of the convex hull for a set of points.

`alg` can either be `GiftWrappingAlg()` or `GrahamScanAlg()`.

For  `n` input vertices and `h` resultant vertices on the convex hull:

  * `GiftWrappingAlg` runs in `O(nh)` time.
  * `GrahamScanAlg` runs in `O(n*log(n))` time.
