```
XPRSgetinfeas(prob, x, slack, duals, djs)::nprimalcols, nprimalrows, ndualrows, ndualcols, x, slack, duals, djs
```

不適合なプライマルおよびデュアル変数のリストを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: プライマル不適合変数が返される長さ `nprimalcols` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: プライマル不適合行が返される長さ `nprimalrows` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: デュアル不適合行が返される長さ `ndualrows` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: デュアル不適合変数が返される長さ `ndualcols` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。

# 戻り値

  * `nprimalcols::Int32`: プライマル不適合変数の数が返される整数へのポインタ。
  * `nprimalrows::Int32`: プライマル不適合行の数が返される整数へのポインタ。
  * `ndualrows::Int32`: デュアル不適合行の数が返される整数へのポインタ。
  * `ndualcols::Int32`: デュアル不適合変数の数が返される整数へのポインタ。
  * `x::Union{Nothing,AbstractVector{Int32}}`: プライマル不適合変数が返される長さ `nprimalcols` の整数配列。
  * `slack::Union{Nothing,AbstractVector{Int32}}`: プライマル不適合行が返される長さ `nprimalrows` の整数配列。
  * `duals::Union{Nothing,AbstractVector{Int32}}`: デュアル不適合行が返される長さ `ndualrows` の整数配列。
  * `djs::Union{Nothing,AbstractVector{Int32}}`: デュアル不適合変数が返される長さ `ndualcols` の整数配列。

C API の対応する関数 [XPRSgetinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetinfeas.html) のドキュメントも参照してください。
