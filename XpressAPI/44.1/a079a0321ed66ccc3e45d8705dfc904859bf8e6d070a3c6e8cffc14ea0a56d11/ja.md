```
XPRSgetcoef(prob, row, col)::coef
```

制約行列の単一の係数を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 制約行列の行。
  * `col::Integer`: 制約行列の列。

# 戻り値

  * `coef::Float64`: 係数が返されるダブルへのポインタ。

C APIの対応する関数[XPRSgetcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcoef.html)のドキュメントも参照してください。
