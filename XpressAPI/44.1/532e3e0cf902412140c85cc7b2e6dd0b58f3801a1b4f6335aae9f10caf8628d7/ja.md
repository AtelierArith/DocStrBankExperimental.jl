```
XPRSgetpresolvesol(prob, x, slack, duals, djs)::x, slack, duals, djs
```

メモリから前処理された問題の解を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: プライマル変数の値が返される長さCOLSのダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: スラック変数の値が返される長さROWSのダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 双対変数の値が返される長さ`ROWS`のダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 各変数の縮小コストが返される長さ`COLS`のダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `x::Union{Nothing,AbstractVector{Float64}}`: プライマル変数の値が返される長さCOLSのダブル配列。
  * `slack::Union{Nothing,AbstractVector{Float64}}`: スラック変数の値が返される長さROWSのダブル配列。
  * `duals::Union{Nothing,AbstractVector{Float64}}`: 双対変数の値が返される長さ`ROWS`のダブル配列。
  * `djs::Union{Nothing,AbstractVector{Float64}}`: 各変数の縮小コストが返される長さ`COLS`のダブル配列。

C APIの対応する関数のドキュメント[XPRSgetpresolvesol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpresolvesol.html)も参照してください。
