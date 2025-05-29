```
get_faceness(feature::HaarLikeObject{I, F}, int_img::IntegralArray{T, N}) -> Number
```

与えられた特徴の顔らしさを取得します。

# 引数

  * `feature::HaarLikeObject`: 与えられたHaar-like特徴（Pythonの`self`のパラメータ化された置き換え）
  * `int_img::IntegralArray`: 積分画像配列

# 戻り値

  * `score::Number`: 与えられた特徴のスコア
