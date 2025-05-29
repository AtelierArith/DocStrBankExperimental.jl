```
XPRSloaddelayedrows(prob, nrows, rowind)::prob
```

ツリー探索中に行列の一部の行を遅延行として扱うことを指定します。

これらは、任意の整数解に対して満たす必要がある行ですが、必要になるまでアクティブな制約のセットには読み込まれません。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 遅延行の数。
  * `rowind::AbstractVector{Integer}`: 遅延行として扱う行インデックスの配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloaddelayedrows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloaddelayedrows.html)のドキュメントも参照してください。
