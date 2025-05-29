```
XPRSgetmqobj(prob, start, colind, objqcoef, maxcoefs, first, last)::start, colind, objqcoef, ncoefs
```

与えられた範囲内の列に対する二次目的係数行列の非ゼロ要素を返します。

最大の効率を達成するために、`XPRSgetmqobj`はこの行列の下三角部分のみを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `start::AbstractVector{Int32}`: 要求された各列の`colind`および`objqcoef`配列における開始オフセットを示すインデックスで埋められる整数配列。
  * `colind::AbstractVector{Int32}`: `Q`の下三角部分における非ゼロ要素の列インデックスで埋められる長さ`maxcoefs`の整数配列。
  * `objqcoef::AbstractVector{Float64}`: 非ゼロ要素の値で埋められる長さ`maxcoefs`の倍精度配列。
  * `maxcoefs::Integer`: 返される要素の最大数（配列のサイズ）。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `start::AbstractVector{Int32}`: 要求された各列の`colind`および`objqcoef`配列における開始オフセットを示すインデックスで埋められる整数配列。
  * `colind::AbstractVector{Int32}`: `Q`の下三角部分における非ゼロ要素の列インデックスで埋められる長さ`maxcoefs`の整数配列。
  * `objqcoef::AbstractVector{Float64}`: 非ゼロ要素の値で埋められる長さ`maxcoefs`の倍精度配列。
  * `ncoefs::Int32`: 非ゼロの二次目的係数の数が返される整数へのポインタ。

C APIの対応する関数のドキュメントも参照してください [XPRSgetmqobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmqobj.html)。
