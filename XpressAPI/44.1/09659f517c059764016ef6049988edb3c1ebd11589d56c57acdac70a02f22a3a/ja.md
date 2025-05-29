```
XPRScalcobjective(prob, solution)::objval
```

与えられた解の目的値を計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `solution::AbstractVector{Number}`: 解を保持する長さCOLSのダブル配列。

# 戻り値

  * `objval::Float64`: 計算された目的値が返されるダブルへのポインタ。

C APIの対応する関数のドキュメント[XPRScalcobjective](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcobjective.html)も参照してください。
