```
XPRSsparseftran(prob, val, ind)::val, ind, ncoefs
```

ユーザーが提供した（列）ベクトルを現在の行列の逆行列で前乗算します。

XPRSftranのスパースバージョンです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `val::AbstractVector{Float64}`: 基底の逆行列で乗算される値を含む長さROWSの倍精度配列。
  * `ind::AbstractVector{Int32}`: `val`の非ゼロエントリを特定する整数配列。

# 戻り値

  * `val::AbstractVector{Float64}`: 基底の逆行列で乗算される値を含む長さROWSの倍精度配列。
  * `ind::AbstractVector{Int32}`: `val`の非ゼロエントリを特定する整数配列。
  * `ncoefs::Int32`: 非ゼロエントリの数が与えられるメモリ位置。

C APIの対応する関数[XPRSsparseftran](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsparseftran.html)のドキュメントも参照してください。
