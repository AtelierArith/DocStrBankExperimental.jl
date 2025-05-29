```
shadow_model(sat_pos::AbstractArray, sun_pos::AbstractArray, R_Sun::Number, R_Occulting::Number, t::Number, ShadowModel::ShadowModelType)
```

地球の影のアンブラとプレナブラからの太陽の照明係数を計算します。

# 引数

  * `sat_pos::AbstractArray`: 現在の衛星の位置。
  * `sun_pos::AbstractArray`: 現在の太陽の位置。
  * `R_Sun::Number`: 太陽の半径。
  * `R_Occulting::Number`: 隠蔽体の半径。
  * `ShadowModel::ShadowModelType`: 使用する地球の影モデル。現在のオプション – 円柱、円錐、円錐_簡略化、なし

# 戻り値

  * `SVector{3}{Number}`: 第三者からの慣性加速度
