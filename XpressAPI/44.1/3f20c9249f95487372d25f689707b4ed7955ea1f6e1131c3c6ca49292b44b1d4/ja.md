```
XPRSgetduals(prob, duals, first, last)::status, duals
```

最適化中または最適化後に、連続問題に関連する双対値を取得するために使用されます。これは、`XPRSoptimize`、`XPRSlpoptimize`、または `XPRSnlpoptimize` を使用します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `duals::Union{XPRSallocatable,AbstractVector{Float64}}`: 双対変数の値が返されるダブルポインタ。適切なサイズの配列を関数が自動的に割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 双対解の最初の行。
  * `last::Integer`: 双対解の最後の行。

# 戻り値

  * `status::Int32`: 返された双対解に関する情報。
  * `duals::AbstractVector{Float64}`: 双対変数の値が返されるダブルポインタ。

C APIの対応する関数 [XPRSgetduals](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetduals.html) のドキュメントも参照してください。
