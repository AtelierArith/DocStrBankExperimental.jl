```
AICc(DM::DataModel, θ::AbstractVector) -> Real
```

Computes Akaike Information Criterion with an added correction term that prevents the AIC from selecting models with too many parameters (i.e. overfitting) in the case of small sample sizes. $\mathrm{AICc} = \mathrm{AIC} + \frac{2\mathrm{length}(\theta)^2 + 2 \mathrm{length}(\theta)}{N - \mathrm{length}(\theta) - 1}$ where $N$ is the number of data points. Whereas AIC constitutes a first order estimate of the information loss, the AICc constitutes a second order estimate. However, this particular correction term assumes that the model is **linearly parametrized**.
