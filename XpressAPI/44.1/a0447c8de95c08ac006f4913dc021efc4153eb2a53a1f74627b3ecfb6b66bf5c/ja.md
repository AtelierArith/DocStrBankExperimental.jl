```
XPRSchgqrowcoeff(prob, row, rowqcol1, rowqcol2, rowqcoef)::prob
```

行の単一の二次係数を変更します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 二次行列を変更する行のインデックス。
  * `rowqcol1::Integer`: 変更する係数の最初のインデックス。
  * `rowqcol2::Integer`: 変更する係数の第二のインデックス。
  * `rowqcoef::Float64`: 新しい係数。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSchgqrowcoeff](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgqrowcoeff.html)。
