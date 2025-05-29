```
XPRSchgrhs(prob, nrows, rowind, rhs)::prob
```

問題の右辺の値を変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 変更する右辺の値の数。
  * `rowind::AbstractVector{Integer}`: 右辺の値が変更される行のインデックスを含む長さ `nrows` の整数配列。
  * `rhs::AbstractVector{Number}`: 右辺の値を与える長さ `nrows` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgrhs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgrhs.html) のドキュメントも参照してください。
