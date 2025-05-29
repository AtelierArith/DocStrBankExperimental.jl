```
XPRSgetpwlcons(prob, colind, resultant, start, xval, yval, maxpoints, first, last)::colind, resultant, start, xval, yval, npoints
```

指定された範囲内の区分線形制約 `y = f(x)` を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 入力変数 `x` のインデックスで埋められる整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `resultant::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 出力変数 `y` のインデックスで埋められる整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `start::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: ブレークポイント配列内の異なる制約の開始インデックスで埋められる整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `xval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: ブレークポイントの `x` 値で埋められる長さ `maxpoints` の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `yval::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: ブレークポイントの `y` 値で埋められる長さ `maxpoints` の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `maxpoints::Integer`: 取得するブレークポイントの最大数。
  * `first::Integer`: 範囲内の最初の区分線形制約。
  * `last::Integer`: 範囲内の最後の区分線形制約。

# 戻り値

  * `colind::Union{Nothing,AbstractVector{Int32}}`: 入力変数 `x` のインデックスで埋められる整数配列。
  * `resultant::Union{Nothing,AbstractVector{Int32}}`: 出力変数 `y` のインデックスで埋められる整数配列。
  * `start::Union{Nothing,AbstractVector{Int32}}`: ブレークポイント配列内の異なる制約の開始インデックスで埋められる整数配列。
  * `xval::Union{Nothing,AbstractVector{Float64}}`: ブレークポイントの `x` 値で埋められる長さ `maxpoints` の倍精度配列。
  * `yval::Union{Nothing,AbstractVector{Float64}}`: ブレークポイントの `y` 値で埋められる長さ `maxpoints` の倍精度配列。
  * `npoints::Int32`: 選択された制約内のブレークポイントの数を返すポインタ。

C API の対応する関数 [XPRSgetpwlcons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpwlcons.html) のドキュメントも参照してください。
