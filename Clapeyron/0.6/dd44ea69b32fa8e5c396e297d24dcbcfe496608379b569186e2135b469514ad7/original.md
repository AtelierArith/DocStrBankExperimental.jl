```
saturation_pressure(model::EoSModel, T)
saturation_pressure(model::EoSModel,T,method::SaturationMethod)
saturation_pressure(model,T,x0::Union{Tuple,Vector})
```

Performs a single component saturation equilibrium calculation, at the specified temperature `T`, of one mol of pure sustance specified by `model` Returns `(p₀, Vₗ, Vᵥ)` where `p₀` is the saturation pressure (in Pa), `Vₗ` is the liquid saturation volume (in m³) and `Vᵥ` is the vapour saturation volume (in m³).

If the calculation fails, returns  `(NaN, NaN, NaN)`

By default, it uses [`ChemPotVSaturation`](@ref)

## Examples:

```julia-repl
julia> pr = PR(["water"])
PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule} with 1 component:
  "water"
Contains parameters: a, b, Tc, Pc, Mw

julia> p,vl,vv = saturation_pressure(pr,373.15) #default, uses Clapeyron.ChemPotVSaturation
(96099.38979351855, 2.2674781912892906e-5, 0.03201681565699426)

julia> p,vl,vv = saturation_pressure(pr,373.15,IsoFugacitySaturation()) #iso fugacity
(96099.38979351871, 2.2674781912892933e-5, 0.03201681565699359)

julia> p,vl,vv = saturation_pressure(pr,373.15,IsoFugacitySaturation(p0 = 1.0e5)) #iso fugacity, with starting point
(96099.38979351871, 2.2674781912892933e-5, 0.03201681565699547)
```
