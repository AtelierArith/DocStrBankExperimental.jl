```julia
mutable struct StepSizeTune{A<:BaytesCore.UpdateBool, F<:AbstractFloat}
```

MCMCアルゴリズムのステップサイズパラメータの調整。

# フィールド

  * `adaption::BaytesCore.UpdateBool`: trueの場合、ステップサイズが適応されます。
  * `dualaverage::BaytesMCMC.DualAverage`: Dualaverage構造体
  * `ϵ::AbstractFloat`: 現在のステップサイズ
