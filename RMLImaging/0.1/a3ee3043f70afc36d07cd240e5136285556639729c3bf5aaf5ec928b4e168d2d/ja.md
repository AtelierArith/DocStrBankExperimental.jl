```
transform_linear_forward(model::AbstractImageModel, x::AbstractArray)
```

入力配列の線形スケール強度マップを対応するモデルパラメータの配列に変換します。これは $transform_linear_forward$ の逆関数であることを意図しています。

# 引数

  * `model::AbstractImageModel`: 画像モデル
  * `x::AbstractArray`: 線形スケール強度マップの配列
