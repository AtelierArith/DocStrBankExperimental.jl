```
TransportVelocityAdami(background_pressure::Real)
```

Transport Velocity Formulation (TVF) to suppress pairing and tensile instability. See [TVF](@ref transport_velocity_formulation) for more details of the method.

# Arguments

  * `background_pressure`: Background pressure. Suggested is a background pressure which is                        on the order of the reference pressure.

!!! note
    There is no need for an artificial viscosity to suppress tensile instability when using `TransportVelocityAdami`. Thus, it is highly recommended to use [`ViscosityAdami`](@ref) as viscosity model, since [`ArtificialViscosityMonaghan`](@ref) leads to bad results.

