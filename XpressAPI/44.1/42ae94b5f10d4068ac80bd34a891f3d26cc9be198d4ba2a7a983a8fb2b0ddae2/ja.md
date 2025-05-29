```
XPRSgetcpcuts64(prob, rowind, ncuts, maxcoefs, cuttype, rowtype, start, colind, cutcoef, rhs)::cuttype, rowtype, start, colind, cutcoef, rhs
```

カットプールからカットを返します。

カットへのポインタのリストを含む配列 `rowind` をルーチンに渡す必要があります。カットの列と要素は、`colind` および `cutcoef` パラメータが指す領域に返されます。カットの列と要素は連続して格納され、各カットの開始点は `start` パラメータが指す領域に返されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowind::AbstractVector{Ptr{Cvoid}}`: カットへのポインタを含む長さ `ncuts` の配列。
  * `ncuts::Integer`: 返されるカットの数。
  * `maxcoefs::Integer`: 返されるカットの列インデックスの最大数。
  * `cuttype::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: カットタイプが返される長さ少なくとも `ncuts` の整数配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を割り当てることができます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `rowtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: カットのセンス（`L`、`G`、または `E`）が返される長さ少なくとも `ncuts` の文字配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を割り当てることができます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。
  * `start::AbstractVector{Int64}`: `colind` および `cutcoef` 配列へのオフセットを含む長さ少なくとも `ncuts+1` の整数配列。
  * `colind::AbstractVector{Int32}`: カットの列インデックスが返される長さ `maxcoefs` の整数配列。
  * `cutcoef::AbstractVector{Float64}`: 行列の値が返される長さ `maxcoefs` の倍精度配列。
  * `rhs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: カットの右辺要素が返される長さ少なくとも `ncuts` の倍精度配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を割り当てることができます。この引数に `nothing` を渡すことで、その情報を照会しないことができます。

# 戻り値

  * `cuttype::Union{Nothing,AbstractVector{Int32}}`: カットタイプが返される長さ少なくとも `ncuts` の整数配列。
  * `rowtype::Union{Nothing,AbstractVector{Cchar}}`: カットのセンス（`L`、`G`、または `E`）が返される長さ少なくとも `ncuts` の文字配列。
  * `start::AbstractVector{Int64}`: `colind` および `cutcoef` 配列へのオフセットを含む長さ少なくとも `ncuts+1` の整数配列。
  * `colind::AbstractVector{Int32}`: カットの列インデックスが返される長さ `maxcoefs` の整数配列。
  * `cutcoef::AbstractVector{Float64}`: 行列の値が返される長さ `maxcoefs` の倍精度配列。
  * `rhs::Union{Nothing,AbstractVector{Float64}}`: カットの右辺要素が返される長さ少なくとも `ncuts` の倍精度配列。

対応する関数のドキュメント [XPRSgetcpcuts64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcpcuts64.html) を C API で参照してください。
