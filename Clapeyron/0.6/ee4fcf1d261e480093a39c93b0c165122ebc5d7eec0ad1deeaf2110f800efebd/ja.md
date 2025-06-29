```
ActivityBubbleTemperature(kwargs...)
```

[`bubble_temperature`](@ref)をアクティビティ係数を使用して計算する関数です。アクティビティ係数モデルでは、逐次代入法を用いて問題を解決します。ヘルムホルツベースのモデルでは、アクティビティ係数のためにチャップマン近似を使用します。

入力:

  * `gas_fug = true`: ソルバーがガスのフガシティ係数を使用するかどうか。`ActivityModel`ではデフォルトで`false`に設定されています。
  * `poynting = true`: ソルバーが液体のフガシティ係数にポインティング補正を使用するかどうか。`ActivityModel`ではデフォルトで`false`に設定されています。
  * `y0 = nothing`: オプション、蒸気相の組成の初期推定
  * `T0 = nothing`: オプション、バブル温度[`K`]の初期推定
  * `vol0 = nothing`: オプション、液体および蒸気相の体積の初期推定
  * `atol = 1e-8`: オプション、非線形方程式系の絶対許容誤差
  * `rtol = 1e-12`: オプション、非線形方程式系の相対許容誤差
  * `itmax_ss = 40`: オプション、逐次代入の最大反復回数
