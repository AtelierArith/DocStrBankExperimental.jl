```
weight(::Type{<:WeightNormalization}, cxr::CharXRay)
```

where `WeightNormalization` is one of the following:

  * `NormalizeByShell` normalizes the sum of all the weights associated with a shell to unity.
  * `NormalizeBySubShell` normalizes the sum of all the weights associated with each sub-shell to unity.
  * `NormalizeToUnity` normalizes intensities such that the most intense line in each shell to 1.0.

Computes a rough estimate of the relative intensity of `cxr` relative to the other characteristic X-rays in its shell, sub-shell etc. The different `WeightNormalization` modes reflect different ways that the `weight(...)` function is used.

The difference between `fluorescenceyield(...)` and `weight(...)` is that

  * fluorescenceyield assumes that a sub-shell in the atom is already ionized
  * weight also considers the relative likelihood of ionization of each sub-shell assuming an overvoltage of 4.0.
