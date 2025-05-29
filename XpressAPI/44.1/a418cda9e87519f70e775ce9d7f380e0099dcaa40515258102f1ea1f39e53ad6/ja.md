```
XPRSchgmcoef(prob, ncoefs, rowind, colind, rowcoef)::prob
```

行列の複数の係数を変更するために使用されます。

既存の係数がない場合は、行列に追加されます。行列の行に多くの係数が追加される場合は、古い行を削除して新しい行を追加する方が効率的です。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncoefs::Integer`: 新しい係数の数。
  * `rowind::AbstractVector{Integer}`: 変更される係数の行インデックスを含む長さ `ncoefs` の整数配列。
  * `colind::AbstractVector{Integer}`: 変更される係数の列インデックスを含む長さ `ncoefs` の整数配列。
  * `rowcoef::AbstractVector{Number}`: 新しい係数値を含む長さ `ncoefs` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgmcoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgmcoef.html) のドキュメントも参照してください。
