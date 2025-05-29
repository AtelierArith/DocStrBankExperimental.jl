```
generate_hologram!(dest, desired, incoming, two_pi_modulation, 
    x_period, y_period, method::Type{T}=BesselJ1) where {T<:HologramMethod}
```

[`generate_hologram`](@ref)と同様ですが、結果を`dest`に書き込みます。
