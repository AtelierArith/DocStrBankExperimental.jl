```
XPRSdelindicators(prob, first, last)::prob
```

インジケーター制約を削除します。

これにより、指定された行が通常の行に変わります（インジケーター変数によって制御されない）。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `first::Integer`: 範囲内の最初の行。
  * `last::Integer`: 範囲内の最後の行（含む）。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSdelindicators](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelindicators.html)のドキュメントも参照してください。
