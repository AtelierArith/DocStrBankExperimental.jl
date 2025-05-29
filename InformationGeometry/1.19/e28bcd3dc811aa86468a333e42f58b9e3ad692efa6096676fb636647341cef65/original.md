```
IsLinear(DM::DataModel, MLE::AbstractVector) -> Bool
```

Checks whether the `model(x,θ)` function is linear with respect to all of its parameters $\theta \in \mathcal{M}$. A componentwise check can be attained via the method `IsLinearParameter(DM)`.
