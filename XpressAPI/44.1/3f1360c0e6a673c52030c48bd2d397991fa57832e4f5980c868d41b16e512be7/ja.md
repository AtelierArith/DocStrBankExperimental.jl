```
XPRSchgmqobj(prob, ncoefs, objqcol1, objqcol2, objqcoef)::prob
```

目的関数の複数の二次係数を変更するために使用されます。

係数のいずれかが既に存在しない場合、新しい係数が目的関数に追加されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncoefs::Integer`: 変更する係数の数。
  * `objqcol1::AbstractVector{Integer}`: 各二次項の最初の変数の列インデックスを含むサイズ `ncol` の整数配列。
  * `objqcol2::AbstractVector{Integer}`: 各二次項の2番目の変数の列インデックスを含むサイズ `ncol` の整数配列。
  * `objqcoef::AbstractVector{Number}`: 係数の新しい値。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgmqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgmqobj.html) のドキュメントも参照してください。
