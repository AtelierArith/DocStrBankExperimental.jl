```
get_vote(feature::HaarLikeObject, int_img::IntegralArray) -> Integer
```

この特徴の投票を与えられた積分画像に対して取得します。

# 引数

  * `feature::HaarLikeObject`: 与えられたHaar-like特徴
  * `int_img::IntegralArray`: 積分画像配列

# 戻り値

  * `vote::Integer`:  1       ⟺ この特徴が肯定的に投票する -1      それ以外
