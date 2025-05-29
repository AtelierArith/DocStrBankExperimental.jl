```
XPRSgetscaledinfeas(prob, x, slack, duals, djs)::nprimalcols, nprimalrows, ndualrows, ndualcols, x, slack, duals, djs
```

元の問題に対するスケーリングされた非実行可能なプライマルおよびデュアル変数のリストを返します。

問題が現在前処理されている場合、関数が返す前に後処理されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: プライマル非実行可能変数が返される長さ `nprimalcols` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: プライマル非実行可能行が返される長さ `nprimalrows` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: デュアル非実行可能行が返される長さ `ndualrows` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: デュアル非実行可能変数が返される長さ `ndualcols` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。

# 戻り値

  * `nprimalcols::Int32`: プライマル非実行可能変数の数。
  * `nprimalrows::Int32`: プライマル非実行可能行の数。
  * `ndualrows::Int32`: デュアル非実行可能行の数。
  * `ndualcols::Int32`: デュアル非実行可能変数の数。
  * `x::Union{Nothing,AbstractVector{Int32}}`: プライマル非実行可能変数が返される長さ `nprimalcols` の整数配列。
  * `slack::Union{Nothing,AbstractVector{Int32}}`: プライマル非実行可能行が返される長さ `nprimalrows` の整数配列。
  * `duals::Union{Nothing,AbstractVector{Int32}}`: デュアル非実行可能行が返される長さ `ndualrows` の整数配列。
  * `djs::Union{Nothing,AbstractVector{Int32}}`: デュアル非実行可能変数が返される長さ `ndualcols` の整数配列。

C API の対応する関数 [XPRSgetscaledinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetscaledinfeas.html) のドキュメントも参照してください。
