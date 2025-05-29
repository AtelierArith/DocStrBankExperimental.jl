```
 normlogpdf(μ, σ, x; ϵ = 1.0f-8)
```

GPU automatic differentiable version for the logpdf function of a univariate normal distribution. Adding an epsilon value to guarantee numeric stability if sigma is exactly zero (e.g. if relu is used in output layer).
