```
XPRSslpchgrowwt(prob, row, weight)::prob
```

行の初期ペナルティエラー重みを設定または変更します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 重みを設定または変更する行のインデックス。
  * `weight::Union{Nothing,Float64}`: 重みの新しい値を保持する倍精度変数のアドレス。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSslpchgrowwt](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgrowwt.html)のドキュメントも参照してください。
