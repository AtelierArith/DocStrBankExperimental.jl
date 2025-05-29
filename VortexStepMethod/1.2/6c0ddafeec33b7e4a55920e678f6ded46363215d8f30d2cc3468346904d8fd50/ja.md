```
ソルバー
```

Vortex Step Methodのメインソルバー構造。参照: [solve](@ref)

# 属性

## 一般設定

  * `aerodynamic_model_type`::Model = VSM: モデルタイプ、参照: [Model](@ref)
  * density::Float64 = 1.225: 空気密度 [kg/m³]
  * `max_iterations`::Int64 = 1500
  * `rtol`::Float64 = 1e-5: 相対誤差
  * `tol_reference_error`::Float64 = 0.001
  * `relaxation_factor`::Float64 = 0.03: 収束のための緩和係数

## ダンピング設定

  * `is_with_artificial_damping`::Bool = false: 人工ダンピングを適用するかどうか
  * `artificial_damping`::NamedTuple{(:k2, :k4), Tuple{Float64, Float64}} = (k2=0.1, k4=0.0): 人工ダンピングパラメータ

## 追加設定

  * `type_initial_gamma_distribution`::InitialGammaDistribution = ELLIPTIC: 参照: [InitialGammaDistribution](@ref)
  * `core_radius_fraction`::Float64 = 1e-20:
  * mu::Float64 = 1.81e-5: 動的粘度 [N·s/m²]
  * `is_only_f_and_gamma_output`::Bool = false: fとgammaのみを出力するかどうか

## 解

sol::VSMSolution = VSMSolution(): [solve!](@ref)を呼び出した結果
