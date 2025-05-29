```
TKEDissipationVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(),
                                  FT = Float64;]
                                  tke_dissipation_equations = TKEDissipationEquations(),
                                  stability_functions = VariableStabilityFunctions(),
                                  minimum_length_scale = StratifiedDisplacementScale(),
                                  maximum_tracer_diffusivity = Inf,
                                  maximum_tke_diffusivity = Inf,
                                  maximum_dissipation_diffusivity = Inf,
                                  maximum_viscosity = Inf,
                                  minimum_tke = 1e-6,
                                  minimum_stratification_number_safety_factor = 0.73,
                                  negative_tke_damping_time_scale = 1minute,
                                  tke_dissipation_time_step = nothing)
```

垂直混合のための `TKEDissipationVerticalDiffusivity` turbulence closure は、2つの変数の予測進化に基づく微小スケールの海洋乱流によるものです：乱流運動エネルギー (TKE) と乱流運動エネルギーの消散。別の場所では、これを「k-ϵ」と呼びます。k-ϵ に関する詳細は、Burchard と Bolding (2001)、Umlauf と Buchard (2003)、および Umlauf と Burchard (2005) を参照してください。

# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()` または `VerticallyImplicitTimeDiscretization()` のいずれか;                        デフォルトは `VerticallyImplicitTimeDiscretization()`。
  * `FT`: 浮動小数点型; デフォルトは `Float64`。

# キーワード引数

  * `maximum_diffusivity`: トレーサー、運動量、および TKE 拡散率の最大値。                        TKEDissipationVerticalDiffusivity が                        あまりにも大きな拡散率を予測する場合に、                        拡散率をクリップするために使用されます。                        デフォルト: `Inf`。
  * `minimum_tke`: 乱流運動エネルギーの最小値。                例えば、内部波の崩壊による混合のために、                「背景」TKE レベルの存在をモデル化するために使用できます。                デフォルト: 1e-9。
  * `negative_tke_damping_time_scale`: TKE の疑似的な負の値に対する減衰時間スケール、                                    通常は TKE 輸送に関連する振動誤差によって                                    生成されます。                                    デフォルト: 1 分。

数値的安定性のために、相対的に短い `negative_turbulent_kinetic_energy_damping_time_scale` または合理的な `minimum_turbulent_kinetic_energy`、またはその両方を持つことをお勧めします。
