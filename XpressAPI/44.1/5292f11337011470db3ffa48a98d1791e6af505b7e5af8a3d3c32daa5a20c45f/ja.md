```
XPRSchgrhsrange(prob, nrows, rowind, rng)::prob
```

問題行列の行の範囲を変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 変更する範囲要素の数。
  * `rowind::AbstractVector{Integer}`: 範囲要素が変更される行のインデックスを含む長さ `nrows` の整数配列。
  * `rng::AbstractVector{Number}`: 範囲値を与える長さ `nrows` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSchgrhsrange](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgrhsrange.html)。
