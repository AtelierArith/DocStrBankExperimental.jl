```
get_model_violation(aces_data::ACESData; projected::Bool = false)
```

Returns the noise model violation z-score for the generalised residual sum of squares corresponding to the noise estimates stored in `aces_data`, given the design also stored in `aces_data`, calculating with the projected gate eigenvalues if `projected` is `true`.
