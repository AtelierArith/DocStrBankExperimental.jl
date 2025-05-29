```
XPRSestimaterowdualranges(prob, nrows, rowind, iterlim, mindual, maxdual)::mindual, maxdual
```

デュアルサイドの範囲感度分析を実行します。つまり、デュアル値の可能な範囲の推定値を計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 分析する行の数。
  * `rowind::AbstractVector{Integer}`: 分析する行のインデックス。
  * `iterlim::Integer`: 行ごとの単体法反復として表現された努力制限。
  * `mindual::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 可能なデュアル範囲の推定下限。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `maxdual::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 可能なデュアル範囲の推定上限。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。

# 戻り値

  * `mindual::Union{Nothing,AbstractVector{Float64}}`: 可能なデュアル範囲の推定下限。
  * `maxdual::Union{Nothing,AbstractVector{Float64}}`: 可能なデュアル範囲の推定上限。

C APIの対応する関数 [XPRSestimaterowdualranges](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSestimaterowdualranges.html) のドキュメントも参照してください。
