```
tracedistance(rho, sigma)
```

Trace distance between `rho` and `sigma`. It is defined as

$$
T(ρ,σ) = \frac{1}{2} \operatorname{tr}\{\sqrt{(ρ - σ)^† (ρ - σ)}\}.
$$

It calls [`tracenorm`](@ref) which in turn either uses [`tracenorm_h`](@ref) or [`tracenorm_nh`](@ref) depending if $ρ-σ$ is hermitian or not.
