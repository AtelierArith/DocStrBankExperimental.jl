```
XPRSaddqmatrix64(prob, row, ncoefs, rowqcol1, rowqcol2, rowqcoef)::prob
```

三つ組によって定義された行に新しい二次行列を追加します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 二次行列を追加する行のインデックス。
  * `ncoefs::Integer`: 二次行列を定義するために使用される三つ組の数。
  * `rowqcol1::AbstractVector{Integer}`: 三つ組の最初のインデックス。
  * `rowqcol2::AbstractVector{Integer}`: 三つ組の第二のインデックス。
  * `rowqcoef::AbstractVector{Number}`: 三つ組の係数。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSaddqmatrix64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddqmatrix64.html)のドキュメントも参照してください。
