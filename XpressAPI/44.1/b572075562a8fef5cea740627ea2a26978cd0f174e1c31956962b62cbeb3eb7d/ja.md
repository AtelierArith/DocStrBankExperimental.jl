```
XPRSgetslacks(prob, slacks, first, last)::status, slacks
```

最適化中または最適化後に、現行の解に関連するスラック値を取得するために使用されます。これは、`XPRSoptimize`、`XPRSmipoptimize`、`XPRSlpoptimize`、または `XPRSnlpoptimize` と共に使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `slacks::Union{XPRSallocatable,AbstractVector{Float64}}`: スラック変数の値が返されるダブルポインタ。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: スラックの最初の行。
  * `last::Integer`: スラックの最後の行。

# 戻り値

  * `status::Int32`: 返されたスラックに関する情報。
  * `slacks::AbstractVector{Float64}`: スラック変数の値が返されるダブルポインタ。

C APIの対応する関数 [XPRSgetslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetslacks.html) のドキュメントも参照してください。
