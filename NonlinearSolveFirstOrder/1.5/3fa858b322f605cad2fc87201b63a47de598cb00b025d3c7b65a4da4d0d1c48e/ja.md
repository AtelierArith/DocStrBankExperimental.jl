```
TrustRegion(;
    concrete_jac = nothing, linsolve = nothing,
    radius_update_scheme = RadiusUpdateSchemes.Simple, max_trust_radius::Real = 0 // 1,
    initial_trust_radius::Real = 0 // 1, step_threshold::Real = 1 // 10000,
    shrink_threshold::Real = 1 // 4, expand_threshold::Real = 3 // 4,
    shrink_factor::Real = 1 // 4, expand_factor::Real = 2 // 1,
    max_shrink_times::Int = 32,
    vjp_autodiff = nothing, autodiff = nothing, jvp_autodiff = nothing
)
```

スパース行列の効率的な処理をサポートする高度なTrustRegion実装で、色分け自動微分および前処理された線形ソルバーを使用しています。大規模で数値的に困難な非線形システム向けに設計されています。

### キーワード引数

  * `radius_update_scheme`: 信頼領域の半径を更新するために使用されるスキーム。デフォルトは`RadiusUpdateSchemes.Simple`です。詳細については[`RadiusUpdateSchemes`](@ref)を参照してください。信頼領域半径の更新スキームに関するレビューについては、[yuan2015recent](@citet)を参照してください。

残りの引数については、[`NonlinearSolveFirstOrder.GenericTrustRegionScheme`](@ref)のドキュメントを参照してください。
