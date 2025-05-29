```
saturation_temperature(model::EoSModel, p, kwargs...)
saturation_temperature(model::EoSModel, p, method::SaturationMethod)
saturation_temperature(model, p, T0::Number)
```

Performs a single component saturation temperature equilibrium calculation, at the specified pressure `T`, of one mol of pure sustance specified by `model`

Returns `(T₀, Vₗ, Vᵥ)` where `p₀` is the saturation Temperature (in K), `Vₗ` is the liquid saturation volume (in m³) and `Vᵥ` is the vapour saturation volume (in m³).

If the calculation fails, returns  `(NaN, NaN, NaN)`

By default, it uses [`AntoineSaturation`](@ref)

## Examples:

julia-repl

```
julia> pr = PR(["water"])
PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule} with 1 component:
  "water"
Contains parameters: a, b, Tc, Pc, Mw

julia> Ts,vl,vv = saturation_temperature(pr,1e5) # AntoineSaturation by default
(374.24014010712983, 2.269760164801948e-5, 0.030849387955737825)

julia> saturation_pressure(pr,Ts)
(100000.00004314569, 2.269760164804427e-5, 0.03084938795785433)
```
