```
SubcellLimiterIDP(equations::AbstractEquations, basis;
                  local_twosided_variables_cons = String[],
                  positivity_variables_cons = String[],
                  positivity_variables_nonlinear = [],
                  positivity_correction_factor = 0.1,
                  local_onesided_variables_nonlinear = [],
                  max_iterations_newton = 10,
                  newton_tolerances = (1.0e-12, 1.0e-14),
                  gamma_constant_newton = 2 * ndims(equations))
```

サブセル不変領域保存（IDP）制限は、[`VolumeIntegralSubcellLimiting`](@ref)と共に使用されます：

  * 保守変数のためのローカル両側ザレサク型制限（`local_twosided_variables_cons`）
  * 保守変数（`positivity_variables_cons`）および非線形変数のための正の制限（`positivity_variables_nonlinear`）
  * 非線形変数のためのローカル片側制限、例えば `entropy_guermond_etal` および `entropy_math` に対して

`local_onesided_variables_nonlinear`を使用します。

これらの3つの制限オプションを使用するには、次の構造を使用します：

***制限される保守変数***は、文字列のベクトルとして渡されます。例えば、`local_twosided_variables_cons = ["rho"]` および `positivity_variables_cons = ["rho"]` のように。***非線形変数***については、必要な変数関数をベクトル内に渡します。正の値を確保するためには、希望する変数を含む単純なベクトルを使用します。例えば、`positivity_variables_nonlinear = [pressure]` のようにします。ローカル片側制限には、要求された境界（`min` または `max`）と組み合わせた変数関数をタプルとして渡します。例えば、Guermond et al. によって修正された特定のエントロピーに対して下限を課すには、`local_onesided_variables_nonlinear = [(Trixi.entropy_guermond_etal, min)]` を使用します。

境界は低次のFV解を使用して計算されます。正の制限器は `positivity_correction_factor` を使用し、`u^new >= positivity_correction_factor * u^FV` となるようにします。非線形変数のローカルおよびグローバル制限は、最大 `max_iterations_newton` 回の反復、相対および絶対許容誤差 `newton_tolerances`、および仮の更新定数 `gamma_constant_newton` を使用したニュートン二分法を使用します（`gamma_constant_newton>=2*d`、ここで `d = #dimensions`）。Pazner (2020) の式 (20) および Rueda-Ramírez et al. (2022) の式 (30) を参照してください。

!!! note
    この制限器と修正コールバック [`SubcellLimiterIDPCorrection`](@ref) は一緒に機能します。コールバックがない場合、修正は行われず、標準の低次FVスキームになります。


## 参考文献

  * Rueda-Ramírez, Pazner, Gassner (2022) サブセル制限戦略による不連続ガレルキンスペクトル要素法 [DOI: 10.1016/j.compfluid.2022.105627](https://doi.org/10.1016/j.compfluid.2022.105627)
  * Pazner (2020) サブセル凸制限を用いた疎不変領域保存不連続ガレルキン法 [DOI: 10.1016/j.cma.2021.113876](https://doi.org/10.1016/j.cma.2021.113876)
