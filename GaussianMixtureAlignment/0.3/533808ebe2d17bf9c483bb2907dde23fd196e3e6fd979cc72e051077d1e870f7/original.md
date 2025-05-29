```
score, tform, nevals = rocs_align_gmms(gmmfixed, gmmmoving; maxevals=1000)
```

Finds the optimal alignment between the two supplied GMMs using steric multipoles, based on the [ROCS alignment algorithm.](https://docs.eyesopen.com/applications/rocs/theory/shape_shape.html)
