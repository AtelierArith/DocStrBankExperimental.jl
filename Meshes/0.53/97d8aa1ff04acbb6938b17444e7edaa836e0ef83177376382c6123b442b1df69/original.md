```
HeldTriangulation([rng]; shuffle=true)
```

Fast Industrial-Strength Triangulation (FIST) of polygons.

This triangulation method is the method behind the famous Mapbox's Earcut library. It is based on a ear clipping algorithm adapted for complex n-gons with holes. It has O(n²) time complexity where n is the number of vertices. In practice it is very efficient due to heuristics implemented in the algorithm.

The option `shuffle` is used to shuffle the order in which ears are clipped. It improves the quality of the triangles, which can be very sliver otherwise. Optionally, specify the random number generator `rng`.

## References

  * Held, M. 1998. [FIST: Fast Industrial-Strength Triangulation of Polygons](https://link.springer.com/article/10.1007/s00453-001-0028-4)
  * Eder et al. 2018. [Parallelized ear clipping for the triangulation and constrained Delaunay triangulation of polygons](https://www.sciencedirect.com/science/article/pii/S092577211830004X)
