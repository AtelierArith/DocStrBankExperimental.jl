```
MeanStdScaling(μ, σ) <: AbstractScaling
```

Linearly scale the data by the statistical mean `μ` and standard deviation `σ`. This is also known as standardization, or the Z score transform.

# Keyword arguments to `apply`

  * `inverse=true`: inverts the scaling (e.g. to reconstruct the unscaled data).
  * `eps=1e-3`: used in place of all 0 values in `σ` before scaling (if `inverse=false`).
