```
XPRSloadpresolvebasis(prob, rowstat, colstat)::prob
```

ユーザーの領域から事前解決された基準を読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowstat::AbstractVector{Integer}`: 各行に関連するスラック、余剰、または人工変数の基準ステータスを含む長さROWSの整数配列。
  * `colstat::AbstractVector{Integer}`: 行列の各列の基準ステータスを含む長さCOLSの整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloadpresolvebasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadpresolvebasis.html)のドキュメントも参照してください。
