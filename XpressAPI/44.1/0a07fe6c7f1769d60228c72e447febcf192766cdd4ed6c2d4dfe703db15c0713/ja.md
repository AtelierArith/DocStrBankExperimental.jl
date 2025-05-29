```
XPRSchgobj(prob, ncols, colind, objcoef)::prob
```

目的関数の係数を変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 変更する目的関数係数要素の数。
  * `colind::AbstractVector{Integer}`: 目的係数が変更される列のインデックスを含む長さ `ncols` の整数配列。
  * `objcoef::AbstractVector{Number}`: 新しい目的関数係数を与える長さ `ncols` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgobj.html) のドキュメントも参照してください。
