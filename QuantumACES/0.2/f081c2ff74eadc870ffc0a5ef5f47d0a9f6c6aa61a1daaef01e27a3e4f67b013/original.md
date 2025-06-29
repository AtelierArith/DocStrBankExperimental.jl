```
AbstractNoiseParameters
```

Noise parameters should be stored in a subtype `T <: AbstractNoiseParameters`.

Noise models should be generated by a method of [`init_gate_probabilities`](@ref), which generates Pauli error probabilities for the supplied gates according to some supplied noise parameters.

# Necessary fields

  * `params::Dict{Symbol, Any}`: Dictionary of the noise parameters.
  * `noise_name::String`: Name of the noise model, which should implicitly describe parameter settings.
