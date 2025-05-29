```
XPRSdelrows(prob, nrows, rowind)::prob
```

行を行列から削除します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 削除する行の数。
  * `rowind::AbstractVector{Integer}`: 削除する行を含む長さ `nrows` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSdelrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelrows.html) のドキュメントも参照してください。
