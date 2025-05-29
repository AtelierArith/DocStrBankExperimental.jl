```
generate_hologram!(dest, desired, incoming, two_pi_modulation, 
    x_period, y_period, method::Type{T}=BesselJ1) where {T<:HologramMethod}
```

Same as [`generate_hologram`](@ref), but writes the result to `dest`.
