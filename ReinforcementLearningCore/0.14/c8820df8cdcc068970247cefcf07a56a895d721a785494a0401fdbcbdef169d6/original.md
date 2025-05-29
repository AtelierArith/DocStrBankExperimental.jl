```
diagnormlogpdf(μ, σ, x; ϵ = 1.0f-8)
```

GPU compatible and automatically differentiable version for the logpdf function of normal distributions with  diagonal covariance. Adding an epsilon value to guarantee numeric stability if sigma is  exactly zero (e.g. if relu is used in output layer). Accepts arguments of the same shape: vectors, matrices or 3D array (with dimension 2 of size 1).
