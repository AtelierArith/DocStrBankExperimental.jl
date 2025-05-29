```
CovGaussianNetwork(;pre=identity, μ, Σ)
```

Returns `μ` and `Σ` when called where μ is the mean and Σ is a covariance matrix. Unlike GaussianNetwork, the output is 3-dimensional.  μ has dimensions `(action_size x 1 x batchsize)` and Σ has dimensions `(action_size x action_size x batchsize)`.  The Σ head of the `CovGaussianNetwork` should not directly return a square matrix but a vector of length `action_size x (action_size + 1) ÷ 2`. This vector will contain elements of the uppertriangular cholesky decomposition of the covariance matrix, which is then reconstructed from it.  Sample from `MvNormal.(μ, Σ)`.
