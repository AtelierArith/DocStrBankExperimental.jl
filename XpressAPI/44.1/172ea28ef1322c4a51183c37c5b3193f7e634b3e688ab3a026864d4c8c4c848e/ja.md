```
XPRSgetmipsol(prob, x, slack)::x, slack
```

**非推奨**XPRSgetsolutionおよびXPRSgetslacksを代わりに使用してください。

最後に見つかったMIPソリューションの解の値を取得するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: プライマル変数の値が返される長さORIGINALCOLSのダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: スラック変数の値が返される長さORIGINALROWSのダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `x::Union{Nothing,AbstractVector{Float64}}`: プライマル変数の値が返される長さORIGINALCOLSのダブル配列。
  * `slack::Union{Nothing,AbstractVector{Float64}}`: スラック変数の値が返される長さORIGINALROWSのダブル配列。

C APIの対応する関数[XPRSgetmipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmipsol.html)のドキュメントも参照してください。
