```
XPRSgetredcosts(prob, djs, first, last)::status, djs
```

最適化中または最適化後に、連続問題の現行解に関連する縮小コストを取得するために使用されます。`XPRSoptimize`、`XPRSlpoptimize`、または `XPRSnlpoptimize` を使用します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: 変数の縮小コストが返されるダブルポインタ。適切なサイズの配列を関数が自動的に割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 縮小コストの最初の列。
  * `last::Integer`: 縮小コストの最後の列。

# 戻り値

  * `status::Int32`: 返された縮小コストに関する情報。
  * `djs::AbstractVector{Float64}`: 変数の縮小コストが返されるダブルポインタ。

C APIの対応する関数 [XPRSgetredcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetredcosts.html) のドキュメントも参照してください。
