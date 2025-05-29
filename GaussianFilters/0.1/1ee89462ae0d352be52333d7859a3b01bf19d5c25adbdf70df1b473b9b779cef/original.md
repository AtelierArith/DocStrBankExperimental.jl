```
unscented_transform_inverse(points::Vector{AbstractVector}, w_μ::Vector,
    w_Σ::Vector)
```

Convert a 2n+1 sigma points and weights back to a single measure for mean and covariance (GaussianBelief).

Uses formulation from ProbRob for α/β parameters on a separate covariance weighting, although this is not necessary.
