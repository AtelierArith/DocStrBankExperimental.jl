```
XPRSgetrhsrange(prob, rng, first, last)::rng
```

指定された範囲内の行の右辺範囲値を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rng::Union{XPRSallocatable,AbstractVector{Float64}}`: 右辺範囲値を配置するための長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 範囲内の最初の行。
  * `last::Integer`: 範囲内の最後の行。

# 戻り値

  * `rng::AbstractVector{Float64}`: 右辺範囲値を配置するための長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetrhsrange](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrhsrange.html) のドキュメントも参照してください。
