```
XPRSftran(prob, vec)::vec
```

ユーザーが提供した（列）ベクトルを現在の行列の逆行列で前乗算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `vec::AbstractVector{Float64}`: 基底の逆行列で乗算される値を含む長さROWSの倍精度配列。

# 戻り値

  * `vec::AbstractVector{Float64}`: 基底の逆行列で乗算される値を含む長さROWSの倍精度配列。

C APIの対応する関数[XPRSftran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSftran.html)のドキュメントも参照してください。
