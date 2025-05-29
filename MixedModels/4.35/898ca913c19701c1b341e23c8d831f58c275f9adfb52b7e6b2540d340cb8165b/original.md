```
issingular(m::MixedModel, θ=m.θ; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps)
```

Test whether the model `m` is singular if the parameter vector is `θ`.

Equality comparisons are used b/c small non-negative θ values are replaced by 0 in `fit!`.

!!! note
    For `GeneralizedLinearMixedModel`, the entire parameter vector (including β in the case `fast=false`) must be specified if the default is not used.

