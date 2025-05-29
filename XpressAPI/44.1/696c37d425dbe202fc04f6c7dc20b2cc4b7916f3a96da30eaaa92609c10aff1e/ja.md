```
XPRSgetrows64(prob, start, colind, colcoef, maxcoefs, first, last)::start, colind, colcoef, ncoefs
```

指定された範囲内の行に対する制約行列の非ゼロ要素を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `start::AbstractVector{Int64}`: 要求された各行の `colind` および `colcoef` 配列における開始オフセットを示すインデックスで埋められる整数配列。
  * `colind::AbstractVector{Int32}`: 各行の非ゼロ要素の列インデックスで埋められる長さ `maxcoefs` の整数配列。
  * `colcoef::AbstractVector{Float64}`: 非ゼロ要素の値で埋められる長さ `maxcoefs` の倍精度配列。
  * `maxcoefs::Integer`: 取得する要素の最大数。
  * `first::Integer`: 範囲内の最初の行。
  * `last::Integer`: 範囲内の最後の行。

# 戻り値

  * `start::AbstractVector{Int64}`: 要求された各行の `colind` および `colcoef` 配列における開始オフセットを示すインデックスで埋められる整数配列。
  * `colind::AbstractVector{Int32}`: 各行の非ゼロ要素の列インデックスで埋められる長さ `maxcoefs` の整数配列。
  * `colcoef::AbstractVector{Float64}`: 非ゼロ要素の値で埋められる長さ `maxcoefs` の倍精度配列。
  * `ncoefs::Int64`: 選択された行の非ゼロ要素の数が返される整数へのポインタ。

C API の対応する関数 [XPRSgetrows64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrows64.html) のドキュメントも参照してください。
