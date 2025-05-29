```
frechet_offests
```

Given P, and subset of indices of P defining a subpolygon, computes a -approximation to the Frechet distance between every edge of the subpolygon they define, and corresponding portion of P.  A fast, and probably decent approximation to the optimal morhping. Finally, set for every vertex of the subcurve, the frechet distance of this subcurve. Thus, providing a fast estimates of the offsets.
