```
SmoothSafetyFilter <: SafetyFilter
```

Smooth controller that approximates CBF-QP arbitrarily closely.

# Fields

  * `formula::String` : string indicating formula used in smooth safety filter
  * `σ::Float64` : smoothing parameter
  * `k::Function` : function that computes safe control actions
