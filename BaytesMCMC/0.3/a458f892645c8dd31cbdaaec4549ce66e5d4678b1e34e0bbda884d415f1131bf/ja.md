```julia
struct ConfigStepnumber{A<:BaytesCore.UpdateBool}
```

ステップサイズ適応のデフォルト設定。

# フィールド

  * `stepnumberadaption::BaytesCore.UpdateBool`: ステップ番号適応
  * `steps::Int64`: 初期ステップ数
  * `maxsteps::Int64`: 最大ステップ数
  * `∫dt::Float64`: 望ましい積分時間
