```
mutable struct RoundRotorQuadratic <: Machine
    base_machine::RoundRotorMachine
    saturation_coeffs::Tuple{Float64, Float64}
```

4-states round-rotor synchronous machine with quadratic saturation: IEEE Std 1110 §5.3.2 (Model 2.2). GENROU model in PSSE and PSLF.

# Arguments

  * `base_machine::RoundRotorMachine`: Round Rotor Machine model.
  * `saturation_coeffs::Tuple{Float64, Float64}``: Saturation coefficients for quadratic model.
