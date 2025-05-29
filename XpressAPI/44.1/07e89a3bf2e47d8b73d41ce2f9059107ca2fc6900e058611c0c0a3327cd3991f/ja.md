```
XPRSslpevaluatecoef(prob, row, col)::value
```

現在の変数の値を使用して係数を評価します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 行の整数インデックス。
  * `col::Integer`: 列の整数インデックス。

# 戻り値

  * `value::Float64`: 計算結果を受け取るための倍精度値のアドレス。

C APIの対応する関数[XPRSslpevaluatecoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpevaluatecoef.html)のドキュメントも参照してください。
