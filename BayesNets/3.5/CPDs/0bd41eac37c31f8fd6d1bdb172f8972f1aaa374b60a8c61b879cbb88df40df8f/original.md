A conditional linear Gaussian CPD, always returns a Normal{Float64}

```
This is a combination of the CategoricalCPD and the LinearGaussianCPD.
For a variable with N discrete parents and M continuous parents, it will construct
a linear gaussian distribution for all M parents for each discrete instantiation.

                  { Normal(μ=a₁×continuous_parents(x) + b₁, σ₁) for discrete instantiation 1
P(x|parents(x)) = { Normal(μ=a₂×continuous_parents(x) + b₂, σ₂) for discrete instantiation 2
                  { ...
```
