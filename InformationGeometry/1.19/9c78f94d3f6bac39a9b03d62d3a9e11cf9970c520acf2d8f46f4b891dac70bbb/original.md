```
EmbeddingMap(DM::AbstractDataModel, θ::AbstractVector{<:Number}) -> Vector
```

Returns a vector of the collective predictions of the `model` as evaluated at the x-values and the parameter configuration $\theta$.

```
h(\theta) \coloneqq \big(y_\mathrm{model}(x_1;\theta),...,y_\mathrm{model}(x_N;\theta)\big) \in \mathcal{D}
```
