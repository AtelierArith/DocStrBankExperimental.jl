```
XPRSgetqrowcoeff(prob, row, rowqcol1, rowqcol2)::rowqcoef
```

与えられた制約のヘッセ行列における変数ペア（`rowqcol1`、`rowqcol2`）に対応する単一の二次制約係数を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 係数を検索する二次行。
  * `rowqcol1::Integer`: 二次項の最初の変数の列インデックス。
  * `rowqcol2::Integer`: 二次項の2番目の変数の列インデックス。

# 戻り値

  * `rowqcoef::Float64`: 目的関数係数が配置されるダブル値へのポインタ。

C APIの対応する関数[XPRSgetqrowcoeff](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrowcoeff.html)のドキュメントも参照してください。
