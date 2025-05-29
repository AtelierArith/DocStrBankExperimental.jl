```
saturation_temperature(model::EoSModel, p, kwargs...)
saturation_temperature(model::EoSModel, p, method::SaturationMethod)
saturation_temperature(model, p, T0::Number)
```

指定された圧力 `T` における、モデルで指定された純物質の1モルの単一成分飽和温度平衡計算を実行します。

返されるのは `(T₀, Vₗ, Vᵥ)` であり、`p₀` は飽和温度（K単位）、`Vₗ` は液体飽和体積（m³単位）、`Vᵥ` は蒸気飽和体積（m³単位）です。

計算が失敗した場合、 `(NaN, NaN, NaN)` を返します。

デフォルトでは、[`AntoineSaturation`](@ref) を使用します。

## 例:

julia-repl

```
julia> pr = PR(["water"])
PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule} with 1 component:
  "water"
Contains parameters: a, b, Tc, Pc, Mw

julia> Ts,vl,vv = saturation_temperature(pr,1e5) # デフォルトでAntoineSaturation
(374.24014010712983, 2.269760164801948e-5, 0.030849387955737825)

julia> saturation_pressure(pr,Ts)
(100000.00004314569, 2.269760164804427e-5, 0.03084938795785433)
```
