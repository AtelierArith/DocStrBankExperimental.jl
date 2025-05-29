```
T_s(n₁, n₂, θᵢ)
T_s(n₁, n₂, θᵢ, θₜ)
```

Calculate the transmittance for s-polarized light, i.e.  the fraction of incident light energy that is transmitted. 

The transmitted angle θₜ defaults to `asin(n₁ / n₂ * sin(θᵢ))`,  which Snell's law states.

# Arguments:

n₁: The refractive index of the original medium n₂: The refractive index of the medium transmitted into θᵢ: The incident angle in radians, meansured from the surface normal θₜ: The transmitted angle in radians, measured  from the surface normal
