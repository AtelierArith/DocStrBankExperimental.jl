```
XPRSchgqobj(prob, objqcol1, objqcol2, objqcoef)::prob
```

目的関数のヘッセ行列に対応する変数ペア `(objqcol1,objqcol2)` の単一の二次係数を変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objqcol1::Integer`: 二次項の最初の変数の列インデックス。
  * `objqcol2::Integer`: 二次項の二番目の変数の列インデックス。
  * `objqcoef::Float64`: 二次ヘッセ行列の係数の新しい値。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgqobj.html) のドキュメントも参照してください。
