```julia
struct ConfigStepsize{A<:BaytesCore.UpdateBool, B<:BaytesCore.UpdateBool}
```

ステップサイズ適応のデフォルト設定。

# フィールド

  * `ϵ::Float64`: 初期離散化サイズ
  * `stepsizeadaption::BaytesCore.UpdateBool`: ステップサイズ適応
  * `initialstepsize::BaytesCore.UpdateBool`: 初期ステップサイズを推定するかどうかのブール値
