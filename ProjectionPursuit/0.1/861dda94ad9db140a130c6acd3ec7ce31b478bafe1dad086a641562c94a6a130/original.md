```
gensphere(N::Int64, d::Int64)
```

Generate low discrepancy sequences of length N on a d dimension unit sphere.

Roughly speaking, a low discrepancy sequence is a sequence of samples of a random variable     has the property that the number of points within a region is proportional to the size     of the region.

This function returns a N-by-d matrix, where each row represents a sample of a random      vector that is uniformly distributed on a d-dimensional unit sphere.

See Brauchart, Johann S., Josef Dick, and Lou Fang.      "Spatial low-discrepancy sequences, spherical cone discrepancy,      and applications in financial modeling."       Journal of Computational and Applied Mathematics 286 (2015): 28-53.
