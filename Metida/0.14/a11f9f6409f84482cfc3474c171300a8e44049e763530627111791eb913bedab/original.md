```
SpatialPower()
```

Spatian Power covariance structure. Used only for repeated effect.

$$
R_{i,j} = \sigma^{2} * \rho^{dist(i,j)}
$$

where `dist` - Euclidean distance between row-vectors of repeated effect matrix for subject `i` and `j`, 1 > ρ > -1.

SPPOW = SpatialPower()
