```
XPRSgetscale(prob, rowscale, colscale)::rowscale, colscale
```

行列の現在のスケーリングを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowscale::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 行のスケーリングに現在使用されている `2` の累乗を含むサイズ ROWS の整数配列。適切なサイズの配列を関数が自動的に割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しない場合は、この引数に `nothing` を渡すことができます。
  * `colscale::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 列のスケーリングに現在使用されている `2` の累乗を含むサイズ COLS の整数配列。適切なサイズの配列を関数が自動的に割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しない場合は、この引数に `nothing` を渡すことができます。

# 戻り値

  * `rowscale::Union{Nothing,AbstractVector{Int32}}`: 行のスケーリングに現在使用されている `2` の累乗を含むサイズ ROWS の整数配列。
  * `colscale::Union{Nothing,AbstractVector{Int32}}`: 列のスケーリングに現在使用されている `2` の累乗を含むサイズ COLS の整数配列。

C API の対応する関数 [XPRSgetscale](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetscale.html) のドキュメントも参照してください。
