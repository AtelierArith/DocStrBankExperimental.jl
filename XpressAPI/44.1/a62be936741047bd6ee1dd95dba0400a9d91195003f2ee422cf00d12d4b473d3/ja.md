```
XPRSgetcallbackduals(prob, duals, first, last)::available, duals
```

現在のコールバックに関連付けられた解から双対値を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `duals::Union{XPRSallocatable,AbstractVector{Float64}}`: 双対変数の値が返される長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 双対値を返す最初の行。
  * `last::Integer`: 双対値を返す最後の行。

# 戻り値

  * `available::Int32`: 双対解が利用可能な場合、この変数は1に設定されます。
  * `duals::AbstractVector{Float64}`: 双対変数の値が返される長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetcallbackduals](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackduals.html) のドキュメントも参照してください。
