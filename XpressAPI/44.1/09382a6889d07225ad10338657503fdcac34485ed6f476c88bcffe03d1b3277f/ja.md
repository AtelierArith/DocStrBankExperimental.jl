```
XPRSchgglblimit(prob, ncols, colind, limit)::prob
```

半連続または半整数の下限、または部分整数の上限を変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 変更する列の制限の数。
  * `colind::AbstractVector{Integer}`: 制限を変更すべき半連続、半整数、または部分整数列のインデックスを含むサイズ `ncols` の整数配列。
  * `limit::AbstractVector{Number}`: 新しい制限値を与える長さ `ncols` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgglblimit](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgglblimit.html) のドキュメントも参照してください。
