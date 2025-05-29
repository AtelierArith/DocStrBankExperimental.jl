```
BIC(DM::DataModel, θ::AbstractVector) -> Real
```

Calculates the Bayesian Information Criterion given a parameter configuration $\theta$ defined by $\mathrm{BIC} = \mathrm{ln}(N) \cdot \mathrm{length}(\theta) -2 \, \ell(\mathrm{data} \, | \, \theta)$ where $N$ is the number of data points.
