```
XPRSgetcols64(prob, start, rowind, rowcoef, maxcoefs, first, last)::start, rowind, rowcoef, ncoefs
```

指定された範囲内の列に対する制約行列の非ゼロ要素を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `start::AbstractVector{Int64}`: 各要求された列の `rowind` および `rowcoef` 配列における開始オフセットを示すインデックスで埋められる整数配列。
  * `rowind::AbstractVector{Int32}`: 各列の非ゼロ係数の行インデックスで埋められる長さ `maxcoefs` の整数配列。
  * `rowcoef::AbstractVector{Float64}`: 非ゼロ係数値で埋められる長さ `maxcoefs` の倍精度配列。
  * `maxcoefs::Integer`: `rowind` および `rowcoef` 配列のサイズ。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `start::AbstractVector{Int64}`: 各要求された列の `rowind` および `rowcoef` 配列における開始オフセットを示すインデックスで埋められる整数配列。
  * `rowind::AbstractVector{Int32}`: 各列の非ゼロ係数の行インデックスで埋められる長さ `maxcoefs` の整数配列。
  * `rowcoef::AbstractVector{Float64}`: 非ゼロ係数値で埋められる長さ `maxcoefs` の倍精度配列。
  * `ncoefs::Int64`: 選択された列の非ゼロ係数の数が返される整数へのポインタ。

C API の対応する関数 [XPRSgetcols64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcols64.html) のドキュメントも参照してください。
