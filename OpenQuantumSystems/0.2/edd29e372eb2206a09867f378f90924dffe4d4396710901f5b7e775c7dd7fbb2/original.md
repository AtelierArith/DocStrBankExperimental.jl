```
tracenorm(rho)
```

Trace norm of `rho`. It is defined as

$$
T(ρ) = \operatorname{tr}\{\sqrt{ρ^† ρ}\}.
$$

Depending if `rho` is hermitian either [`tracenorm_h`](@ref) or [`tracenorm_nh`](@ref) is called.
