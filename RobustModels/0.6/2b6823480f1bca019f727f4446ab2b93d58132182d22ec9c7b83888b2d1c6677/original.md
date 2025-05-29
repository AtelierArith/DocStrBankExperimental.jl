```
vcov(m::RobustLinearModel, variant::Symbol)
```

Returns `vcov` for the model using a different weights vector depending on the variant:     - `variant = :original`: use the user-defined weights, if no weights were used         (size of the weights vector is 0), no weights are used.     - `variant = :fitted`: use the working weights of the fitted model from the IRLS         procedure.
