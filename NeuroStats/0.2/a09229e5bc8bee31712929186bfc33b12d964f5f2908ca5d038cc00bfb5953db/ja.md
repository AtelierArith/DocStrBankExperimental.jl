```
mscr(; <keyword arguments>)
```

分類モデルのパフォーマンスを誤分類率を使用して評価します。

# 引数

  * `tp::Int64`: 真陽性の数
  * `tn::Int64`: 真陰性の数
  * `fp::Int64`: 偽陽性の数
  * `fn::Int64`: 偽陰性の数

# 戻り値

名前付きタプルを含む:

  * `mr::Float64`: 誤分類率
  * `acc::Float64`: 精度

# ソース

https://www.statology.org/misclassification-rate/
