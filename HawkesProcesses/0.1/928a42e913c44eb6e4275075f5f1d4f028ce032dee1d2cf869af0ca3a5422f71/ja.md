```
intensity(ts, events, background, kappa, kernel)
```

観測されたイベントに対して与えられたホークスパラメータで時間グリッド上の強度を評価します。

# 引数

  * `ts::Array{<:Number,1}`: 強度を評価するための時間グリッド
  * `events::Array{<:Number,1}`: プロセスのイベント
  * `background`: バックグラウンドレート
  * `kappa::Float64`: カッパ値
  * `kernel::Function`: カーネル関数

# 注意事項

  * `kappa` は 0 と 1 の間でなければなりません。
