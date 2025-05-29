```
TunableQPSafetyFilter(cbfs::Vector{ControlBarrierFunction}, Σ::ControlAffineSystem, kd::Function; tunable=false)
```

Construct an TunableQPSafetyFilter from a cbf and a desired controller.

# Keywork arguments

  * `tunable::Bool` : boolean to decide if coefficients on extended class K functions should be decision variables
