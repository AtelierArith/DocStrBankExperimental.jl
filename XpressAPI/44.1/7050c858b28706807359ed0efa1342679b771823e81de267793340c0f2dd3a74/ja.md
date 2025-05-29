```
XPRScalcreducedcosts(prob, duals, solution, djs)::djs
```

与えられた（行）双対解に対する削減コスト値を計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `duals::AbstractVector{Number}`: 削減コストを計算するための双対解を保持する長さROWSの倍精度配列。
  * `solution::AbstractVector{Number}`: プライマル解を保持する長さCOLSのオプションの倍精度配列。
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: 計算された削減コストが返される長さCOLSの倍精度配列。この引数には、関数が適切なサイズの配列を割り当てるために`XPRS_ALLOC`を渡すことができます。

# 戻り値

  * `djs::AbstractVector{Float64}`: 計算された削減コストが返される長さCOLSの倍精度配列。

C APIの対応する関数[XPRScalcreducedcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcreducedcosts.html)のドキュメントも参照してください。
