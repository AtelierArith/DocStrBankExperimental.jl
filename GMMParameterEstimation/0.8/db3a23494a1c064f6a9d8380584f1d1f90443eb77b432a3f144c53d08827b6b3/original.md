```
generateGaussians(d::Integer, k::Integer, diagonal::Bool)
```

Generate means and covariances for `k` Gaussians with dimension `d`.

`diagonal` should be true for spherical case, and false for general covariance matrices.
