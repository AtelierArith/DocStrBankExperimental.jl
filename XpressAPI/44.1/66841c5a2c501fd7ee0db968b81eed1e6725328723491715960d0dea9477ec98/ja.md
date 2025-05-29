```
XPRSpostsolvesol(prob, prex, origx)::origx
```

プレスolved空間で定式化されたプライマルソリューションを、元の空間で定式化された対応するソリューションにポストソルブします。

問題自体は変更されません。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `prex::AbstractVector{Number}`: プレスolved空間におけるプライマル変数の値を持つ長さCOLSのダブル配列。
  * `origx::Union{XPRSallocatable,AbstractVector{Float64}}`: プライマル変数の値が返される長さORIGINALCOLSのダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。

# 戻り値

  * `origx::AbstractVector{Float64}`: プライマル変数の値が返される長さORIGINALCOLSのダブル配列。

C APIの対応する関数[XPRSpostsolvesol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSpostsolvesol.html)のドキュメントも参照してください。
