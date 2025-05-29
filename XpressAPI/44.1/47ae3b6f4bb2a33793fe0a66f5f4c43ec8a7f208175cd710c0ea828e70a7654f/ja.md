```
XPRSgetpivots(prob, enter, outlist, x, maxpivots)::outlist, x, objval, npivots
```

指定された変数が基準に入る場合の潜在的な離脱変数のリストを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `enter::Integer`: 基準に入る指定された行または列のインデックス。
  * `outlist::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 潜在的な離脱変数のリストを保持するための長さが少なくとも `maxpivots` の整数配列。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: `enter` が基準に入った場合に結果として得られるすべての変数の値を保持するための長さ `ROWS`+`SPAREROWS`+`COLS` の倍精度配列。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `maxpivots::Integer`: 返す潜在的な離脱変数の最大数。

# 戻り値

  * `outlist::Union{Nothing,AbstractVector{Int32}}`: 潜在的な離脱変数のリストを保持するための長さが少なくとも `maxpivots` の整数配列。
  * `x::Union{Nothing,AbstractVector{Float64}}`: `enter` が基準に入った場合に結果として得られるすべての変数の値を保持するための長さ `ROWS`+`SPAREROWS`+`COLS` の倍精度配列。
  * `objval::Float64`: `enter` が基準に入った場合に得られる目的関数の値が返される倍精度のポインタ。
  * `npivots::Int32`: 実際の潜在的な離脱変数の数が返される整数のポインタ。

C API の対応する関数 [XPRSgetpivots](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpivots.html) のドキュメントも参照してください。
