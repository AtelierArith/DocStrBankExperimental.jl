```
XPRSchgbounds(prob, nbounds, colind, bndtype, bndval)::prob
```

列の境界を変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nbounds::Integer`: 変更する境界の数。
  * `colind::AbstractVector{Integer}`: 境界が変更される列のインデックスを含むサイズ `nbounds` の整数配列。
  * `bndtype::AbstractVector{Cchar}`: 変更する境界のタイプを示す長さ `nbounds` の文字配列：Uは上限を変更することを示し、Lは下限を変更することを示し、Bは両方の境界を変更すること、すなわち列を固定することを示します。
  * `bndval::AbstractVector{Number}`: 新しい境界値を与える長さ `nbounds` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメント [XPRSchgbounds](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgbounds.html) も参照してください。
