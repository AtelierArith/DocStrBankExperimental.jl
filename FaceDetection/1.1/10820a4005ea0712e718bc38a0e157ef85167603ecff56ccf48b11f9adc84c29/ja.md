```
get_score(feature::HaarLikeObject, int_img::AbstractArray) -> Tuple{Number, Number}
```

与えられた積分画像配列のスコアを取得します。これが特徴カスケードです。

# 引数

  * `feature::HaarLikeObject`: 与えられたHaar-like特徴（Pythonの`self`のパラメータ化された置き換え）
  * `int_img::AbstractArray`: 積分画像配列

# 戻り値

  * `score::Number`: 与えられた特徴のスコア
