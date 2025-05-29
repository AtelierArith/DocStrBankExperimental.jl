```
XPRSbtran(prob, vec)::vec
```

ユーザーが提供した（行）ベクトルを現在の基底の逆行列で右側から乗算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `vec::AbstractVector{Float64}`: 基底の逆行列で乗算される値を含む長さROWSの倍精度配列。

# 戻り値

  * `vec::AbstractVector{Float64}`: 基底の逆行列で乗算される値を含む長さROWSの倍精度配列。

C APIの対応する関数[XPRSbtran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbtran.html)のドキュメントも参照してください。
