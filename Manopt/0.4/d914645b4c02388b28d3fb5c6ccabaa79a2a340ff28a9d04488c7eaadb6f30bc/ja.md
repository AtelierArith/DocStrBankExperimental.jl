```
StopWhenResidualIsReducedByFactorOrPower <: StoppingCriterion
```

現在の反復における残差のノルムが、初期残差のノルムに対して1+θの累乗または因子κによって減少しているかをテストするファンクタです。したがって、基準は次のようになります：$\Vert r_k \Vert_p \leqq \Vert r_0 \Vert_p \min \bigl( \kappa, \Vert r_0 \Vert_p^θ \bigr)$。

# フィールド

  * `κ`:      減少因子
  * `θ`:      減少累乗の一部
  * `reason`: 停止基準が達成された場合の停止理由を格納します。詳細は[`get_reason`](@ref)を参照してください。

# コンストラクタ

```
StopWhenResidualIsReducedByFactorOrPower(; κ=0.1, θ=1.0)
```

現在の残差のノルムが、初期残差のノルムの1+θの累乗または初期残差のノルムにκを掛けたものよりも小さい場合に停止することを示すために、StopWhenResidualIsReducedByFactorOrPowerファンクタを初期化します。

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
