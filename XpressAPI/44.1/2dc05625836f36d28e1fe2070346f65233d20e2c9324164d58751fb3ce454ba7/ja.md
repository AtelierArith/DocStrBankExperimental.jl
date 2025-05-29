```
XPRSchgcoef(prob, row, col, coef)::prob
```

行列の単一の係数を変更するために使用されます。

係数がすでに存在しない場合、新しい係数が行列に追加されます。行列の行に多くの係数を追加する場合、古い行を削除して新しい行を追加する方が効率的かもしれません。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 係数の行インデックス。
  * `col::Integer`: 係数の列インデックス。
  * `coef::Float64`: 係数の新しい値。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSchgcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgcoef.html)のドキュメントも参照してください。
