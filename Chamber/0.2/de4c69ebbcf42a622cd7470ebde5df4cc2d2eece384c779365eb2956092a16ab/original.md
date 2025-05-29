```
rc_f(;rho_x::T, eps_x::T, c_x::T, rho_m::T, eps_m::T, c_m::T, rho_g::T, eps_g::T, c_g::T)::T where {T<:Float64}
```

Computing the product of density and specific heat 

  * This function is used within the `build_rho_rc` function.

## Returns

  * `rc`: the product of density and specific heat
