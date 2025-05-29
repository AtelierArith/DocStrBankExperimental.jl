```
XPRSpivot(prob, enter, leave)::prob
```

変数 `enter` を基底に持ち込み、`leave` を削除することによって単体ピボットを実行します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `enter::Integer`: 基底に入る行または列のインデックス。
  * `leave::Integer`: 基底から出る行または列のインデックス。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSpivot](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSpivot.html) のドキュメントも参照してください。
