```
LevenbergMarquardt(;
    linsolve = nothing,
    damping_initial::Real = 1.0, α_geodesic::Real = 0.75, disable_geodesic = Val(false),
    damping_increase_factor::Real = 2.0, damping_decrease_factor::Real = 3.0,
    finite_diff_step_geodesic = 0.1, b_uphill::Real = 1.0, min_damping_D::Real = 1e-8,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

高度なLevenberg-Marquardtの実装で、[transtrum2012improvements](@citet)で提案された改善が含まれています。大規模で数値的に困難な非線形システム向けに設計されています。

### キーワード引数

  * `damping_initial`: ダンピング係数の初期値。ダンピング係数はステップサイズに反比例します。ダンピング係数は各イテレーション中に調整されます。デフォルトは`1.0`です。[transtrum2012improvements](@citet)のセクション2.1を参照してください。
  * `damping_increase_factor`: ステップが拒否された場合にダンピングが増加する係数。デフォルトは`2.0`です。[transtrum2012improvements](@citet)のセクション2.1を参照してください。
  * `damping_decrease_factor`: ステップが受け入れられた場合にダンピングが減少する係数。デフォルトは`3.0`です。[transtrum2012improvements](@citet)のセクション2.1を参照してください。
  * `min_damping_D`: ダイアゴナルダンピング行列`DᵀD`のダンピング項の最小値。`DᵀD`は、これまでに遭遇した`JᵀJ`の最大の対角成分によって与えられ、`J`はヤコビアンです。[transtrum2012improvements](@citet)では、ダンピングが小さすぎないように`DᵀD`の要素の最小値を使用することが推奨されています。デフォルトは`1e-8`です。
  * `disable_geodesic`: `Val(true)`に設定すると、測地線加速が無効になります。これは、堅牢性と速度のトレードオフを提供しますが、ほとんどの状況では測地線加速を無効にするべきではありません。

残りの引数については、[`GeodesicAcceleration`](@ref)および[`NonlinearSolveFirstOrder.LevenbergMarquardtTrustRegion`](@ref)のドキュメントを参照してください。
