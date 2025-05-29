```
XPRSdelcols(prob, ncols, colind)::prob
```

行列から列を削除します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 削除する列の数。
  * `colind::AbstractVector{Integer}`: 削除する列を含む長さ `ncols` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSdelcols](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelcols.html)。
