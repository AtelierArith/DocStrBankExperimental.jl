```
ISSfSmoothSafetyFilter <: SafetyFilter
```

Smooth controller that approximates an input-to-state safe (ISSf) CBF-QP arbitrarily closely.

# Fields

  * `formula::String` : string indicating formula used in smooth safety filter
  * `σ::Float64` : smoothing parameter
  * `k::Function` : function that computes safe control actions
  * `ε::Float64` : Issf robustness parameter for matched uncertainties
