```
XPRSloadbranchdirs(prob, ncols, colind, dir)::prob
```

現在の問題に指示を読み込み、ノード解が整数的に実現可能な場合にオプティマイザがどのMIPエンティティに対して分岐を続けるべきかを指定します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 指示の数。
  * `colind::AbstractVector{Integer}`: 列番号を含む長さ `ncols` の整数配列。
  * `dir::AbstractVector{Integer}`: `colind` に与えられたエンティティに対して0または1を含む長さ `ncols` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSloadbranchdirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadbranchdirs.html) のドキュメントも参照してください。
