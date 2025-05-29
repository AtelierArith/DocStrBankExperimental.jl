```
StopWhenResidualIsReducedByFactorOrPower <: StoppingCriterion
```

現在の反復における残差のノルムが、初期残差のノルムに対して1+θの累乗または因子κによって減少しているかどうかをテストするファンクタです。したがって、基準は次のようになります。

$$
\lVert r_k \rVert_{p} ≦ \lVert r_0 \rVert_{p^{(0)}} \min \bigl( κ, \lVert r_0 \rVert_{p^{(0)}}  \bigr)
$$

。

# フィールド

  * `κ`:      減少因子
  * `θ`:      減少の累乗の一部
  * `at_iteration::Int`: 停止基準が最後に停止を示した反復を示す整数。これはソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します。

# コンストラクタ

```
StopWhenResidualIsReducedByFactorOrPower(; κ=0.1, θ=1.0)
```

現在の残差のノルムが、初期残差のノルムの1+θの累乗または初期残差のノルムにκを掛けたものよりも小さい場合に停止することを示すために、StopWhenResidualIsReducedByFactorOrPowerファンクタを初期化します。

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
