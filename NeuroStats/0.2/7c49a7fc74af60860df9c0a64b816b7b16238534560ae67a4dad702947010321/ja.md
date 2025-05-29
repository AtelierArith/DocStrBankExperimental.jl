```
mcc(; <keyword arguments>)
```

マシューズ相関係数 (MCC) を使用して分類モデルのパフォーマンスを評価します。

MCCの値は-1から1の範囲で、次のように決まります：

  * -1のスコアは、期待されるクラスと実際のクラスの間に完全な不一致があることを示します
  * 0は、完全に任意の推測を行うことと同等です
  * 期待されるクラスと実際のクラスの間に完全な一致があることは、1のスコアで示されます

# 引数

  * `tp::Int64`: 真陽性の数
  * `tn::Int64`: 真陰性の数
  * `fp::Int64`: 偽陽性の数
  * `fn::Int64`: 偽陰性の数

# 戻り値

  * `mcc::Float64`

# ソース

https://finnstats.com/index.php/2022/09/06/assess-performance-of-the-classification-model/
