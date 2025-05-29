```
SpatialGaussian()
```

Spatian Gaussian covariance structure. Used only for repeated effect.

$$
R_{i,j} = \sigma^{2} * exp(- dist(i,j)^2 / \theta^2)
$$

where `dist` - Euclidean distance between row-vectors of repeated effect matrix for subject `i` and `j`, θ ≠ 0.

SPGAU = SpatialGaussian()
