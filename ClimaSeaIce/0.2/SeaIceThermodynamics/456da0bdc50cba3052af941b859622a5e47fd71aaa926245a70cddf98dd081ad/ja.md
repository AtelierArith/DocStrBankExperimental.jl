```
PhaseTransitions(FT=Float64,
                 ice_density           = 917,   # kg m⁻³
                 ice_heat_capacity     = 2000,  # J / (kg ᵒC)
                 liquid_density        = 999.8, # kg m⁻³
                 liquid_heat_capacity  = 4186,  # J / (kg ᵒC)
                 reference_latent_heat = 334e3  # J kg⁻³
                 liquidus = LinearLiquidus(FT)) # default assumes psu, ᵒC
```

海水の固体と液体の相の間の遷移、つまり海氷の凍結と融解の表現を返します。

融解の潜熱 $ℒ(T)$（より単純に「潜熱」と呼ばれる）は、温度 $T$ の関数であり、

$$
ρᵢ ℒ(T) = ρᵢ ℒ₀ + (ρ_ℓ c_ℓ - ρᵢ cᵢ) (T - T₀)    
$$

ここで、$ρᵢ$ は `ice_density`、$ρ_ℓ$ は液体密度、$cᵢ$ は氷の比熱、$c_ℓ$ は液体の比熱、$T₀$ は基準温度であり、すべては定数であると仮定されています。

デフォルトの `liquidus` は、塩分濃度が実用的塩分単位（psu）であり、温度が摂氏度であると仮定しています。
