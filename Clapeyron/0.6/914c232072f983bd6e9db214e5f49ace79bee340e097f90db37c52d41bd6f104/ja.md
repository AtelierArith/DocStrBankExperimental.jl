```
IsoFugacitySaturation <: SaturationMethod
IsoFugacitySaturation(;p0 = nothing,
    vl = nothing,
    vv = nothing,
    crit = nothing,
    max_iters = 20,
    p_tol = sqrt(eps(Float64)))
```

`saturation_pressure`のための飽和法。イソフガシティ基準を使用します。体積計算が安価な立方体または他のEoSに理想的です。`p0`が提供されていない場合、[`x0_psat`](@ref)を介して計算されます。
