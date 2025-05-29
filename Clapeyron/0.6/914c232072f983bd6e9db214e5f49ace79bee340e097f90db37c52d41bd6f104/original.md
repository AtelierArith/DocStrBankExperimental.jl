```
IsoFugacitySaturation <: SaturationMethod
IsoFugacitySaturation(;p0 = nothing,
    vl = nothing,
    vv = nothing,
    crit = nothing,
    max_iters = 20,
    p_tol = sqrt(eps(Float64)))
```

Saturation method for `saturation_pressure`. Uses the isofugacity criteria. Ideal for Cubics or other EoS where the volume calculations are cheap.  If `p0` is not provided, it will be calculated via [`x0_psat`](@ref).
