```
XPRSgetlb(prob, lb, first, last)::lb
```

指定された範囲内の列の下限を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `lb::Union{XPRSallocatable,AbstractVector{Float64}}`: 下限を配置するための長さ `last-first+1` のダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `lb::AbstractVector{Float64}`: 下限を配置するための長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetlb](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetlb.html) のドキュメントも参照してください。
