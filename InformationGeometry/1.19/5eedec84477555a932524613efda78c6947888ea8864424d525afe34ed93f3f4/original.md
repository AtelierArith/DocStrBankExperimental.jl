```
FisherMetric(DM::DataModel, θ::AbstractVector{<:Number})
```

Computes the Fisher metric $g$ given a `DataModel` and a parameter configuration $\theta$ under the assumption that the likelihood $L(\mathrm{data} \, | \, \theta)$ is a multivariate normal distribution.

$$
g_{ab}(\theta) \coloneqq -\int_{\mathcal{D}} \mathrm{d}^m y_{\mathrm{data}} \, L(y_{\mathrm{data}} \,|\, \theta) \, \frac{\partial^2 \, \mathrm{ln}(L)}{\partial \theta^a \, \partial \theta^b} = -\mathbb{E} \bigg( \frac{\partial^2 \, \mathrm{ln}(L)}{\partial \theta^a \, \partial \theta^b} \bigg)
$$
