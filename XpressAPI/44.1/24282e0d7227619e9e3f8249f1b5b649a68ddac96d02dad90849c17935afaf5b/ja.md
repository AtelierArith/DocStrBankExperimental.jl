```
XPRSgetindicators(prob, colind, complement, first, last)::colind, complement
```

指定された範囲内の行に関連付けられたインジケーター制約条件（インジケーター変数と補完フラグ）を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: インジケーター変数の列インデックスを配置するための長さ `last-first+1` の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `complement::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: インジケーター補完フラグが返される長さ `last-first+1` の整数配列：0はインジケーター制約ではない（この場合、`colind` 配列の対応するエントリは無視されます）；1は条件 "`bin = 1`" のインジケーター制約；-1は条件 "`bin = 0`" のインジケーター制約。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。この情報を照会しないために、この引数に `nothing` を渡すこともできます。
  * `first::Integer`: 範囲内の最初の行。
  * `last::Integer`: 範囲内の最後の行（含む）。

# 戻り値

  * `colind::Union{Nothing,AbstractVector{Int32}}`: インジケーター変数の列インデックスを配置するための長さ `last-first+1` の整数配列。
  * `complement::Union{Nothing,AbstractVector{Int32}}`: インジケーター補完フラグが返される長さ `last-first+1` の整数配列：0はインジケーター制約ではない（この場合、`colind` 配列の対応するエントリは無視されます）；1は条件 "`bin = 1`" のインジケーター制約；-1は条件 "`bin = 0`" のインジケーター制約。

C API の対応する関数 [XPRSgetindicators](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetindicators.html) のドキュメントも参照してください。
