```
IsLinearParameter(DM::DataModel, MLE::AbstractVector) -> BitVector
```

Checks with respect to which parameters the model function `model(x,θ)` is linear and returns vector of booleans where `true` indicates linearity. This test is performed by comparing the Jacobians of the model for two random configurations $\theta_1, \theta_2 \in \mathcal{M}$ column by column.
