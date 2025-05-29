```
XPRSbndsa(prob, ncols, colind, lblower, lbupper, ublower, ubupper)::lblower, lbupper, ublower, ubupper
```

指定された変数の下限および上限の感度範囲を返します。

これらの範囲内で境界が変化すると、現在の基準は最適かつ実行可能なままです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 感度を求める変数の数。
  * `colind::AbstractVector{Integer}`: 境界の範囲が必要な列のインデックスを含む長さ `ncols` の整数配列。
  * `lblower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 変数の下限下範囲値が返される長さ `ncols` の倍精度配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `lbupper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 変数の下限上範囲値が返される長さ `ncols` の倍精度配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `ublower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 変数の上限下範囲値が返される長さ `ncols` の倍精度配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `ubupper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 変数の上限上範囲値が返される長さ `ncols` の倍精度配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。

# 戻り値

  * `lblower::Union{Nothing,AbstractVector{Float64}}`: 変数の下限下範囲値が返される長さ `ncols` の倍精度配列。
  * `lbupper::Union{Nothing,AbstractVector{Float64}}`: 変数の下限上範囲値が返される長さ `ncols` の倍精度配列。
  * `ublower::Union{Nothing,AbstractVector{Float64}}`: 変数の上限下範囲値が返される長さ `ncols` の倍精度配列。
  * `ubupper::Union{Nothing,AbstractVector{Float64}}`: 変数の上限上範囲値が返される長さ `ncols` の倍精度配列。

C API の対応する関数 [XPRSbndsa](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbndsa.html) のドキュメントも参照してください。
