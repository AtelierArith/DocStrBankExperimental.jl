```
transform_linear_forward(model::AbstractImageModel, x::AbstractArray)
```

画像モデルパラメータの入力配列を対応する線形スケール強度マップの配列に変換します。これは $transform_linear_inverse$ の逆関数であるべきです。

# 引数

  * `model::AbstractImageModel`: 画像モデル
  * `x::AbstractArray`: 画像モデルパラメータの配列
