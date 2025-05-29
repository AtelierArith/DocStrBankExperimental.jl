```
XPRSchgcoltype(prob, ncols, colind, coltype)::prob
```

指定された列のセットのタイプを変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 変更する列の数。
  * `colind::AbstractVector{Integer}`: 列のインデックスを含む長さ `ncols` の整数配列。
  * `coltype::AbstractVector{Cchar}`: 新しい列のタイプを示す長さ `ncols` の文字配列：Cは連続列を示し、Bはバイナリ列を示し、Iは整数列を示します。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSchgcoltype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgcoltype.html)。
