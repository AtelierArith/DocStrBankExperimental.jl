```
AIC(DM::DataModel, θ::AbstractVector) -> Real
```

Calculates the Akaike Information Criterion given a parameter configuration $\theta$ defined by $\mathrm{AIC} = 2 \, \mathrm{length}(\theta) -2 \, \ell(\mathrm{data} \, | \, \theta)$. Lower values for the AIC indicate that the associated model function is more likely to be correct. For linearly parametrized models and small sample sizes, it is advisable to instead use the AICc which is more accurate.
