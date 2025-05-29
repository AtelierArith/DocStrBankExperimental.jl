```
saturation_pressure(model::EoSModel, T)
saturation_pressure(model::EoSModel,T,method::SaturationMethod)
saturation_pressure(model,T,x0::Union{Tuple,Vector})
```

指定された温度 `T` で、`model` で指定された純物質の1モルの単成分飽和平衡計算を実行します。戻り値は `(p₀, Vₗ, Vᵥ)` で、`p₀` は飽和圧力（Pa）、`Vₗ` は液体飽和体積（m³）、`Vᵥ` は蒸気飽和体積（m³）です。

計算が失敗した場合、 `(NaN, NaN, NaN)` を返します。

デフォルトでは、[`ChemPotVSaturation`](@ref) を使用します。

## 例:

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
