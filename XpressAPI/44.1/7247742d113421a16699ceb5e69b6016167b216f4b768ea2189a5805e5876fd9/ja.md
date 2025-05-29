```
XPRSgetqobj(prob, objqcol1, objqcol2)::objqcoef
```

変数ペア `(objqcol1, objqcol2)` に対応する単一の二次目的関数係数をヘッセ行列から返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objqcol1::Integer`: 二次項の最初の変数の列インデックス。
  * `objqcol2::Integer`: 二次項の二番目の変数の列インデックス。

# 戻り値

  * `objqcoef::Float64`: 目的関数係数が配置されるダブル値へのポインタ。

C APIの対応する関数 [XPRSgetqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqobj.html) のドキュメントも参照してください。
