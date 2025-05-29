```
mutable struct SalientPoleQuadratic <: Machine
    base_machine::SalientPoleMachine
    saturation_coeffs::Tuple{Float64, Float64}
```

3-states salient-pole synchronous machine with exponential saturation: IEEE Std 1110 §5.3.2 (Model 2.1). GENSAL in PSSE and PSLF.

# Arguments:

  * `base_machine::SalientPoleMachine`: Salient Pole Machine model.
  * `saturation_coeffs::Tuple{Float64, Float64}``: Saturation coefficients for quadratic model.
