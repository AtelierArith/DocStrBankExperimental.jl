```
XPRSnlpdelformulas(prob, nformulas, rowind)::prob
```

現在の問題から非線形式を削除します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `nformulas::Integer`: 削除するSLP非線形式の数。
  * `rowind::AbstractVector{Integer}`: 削除するSLP非線形式の行インデックス。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSnlpdelformulas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpdelformulas.html)のドキュメントも参照してください。
