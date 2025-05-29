```
XPRSgetbasis(prob, rowstat, colstat)::rowstat, colstat
```

ユーザーのデータ配列に現在の基準を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowstat::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 各行に関連するスラック、余剰、または人工変数の基準ステータスのための長さ ORIGINALROWS の整数配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すことで、その情報を照会しないこともできます。
  * `colstat::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 制約行列の列の基準ステータスを保持するための長さ ORIGINALCOLS の整数配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すことで、その情報を照会しないこともできます。

# 戻り値

  * `rowstat::Union{Nothing,AbstractVector{Int32}}`: 各行に関連するスラック、余剰、または人工変数の基準ステータスのための長さ ORIGINALROWS の整数配列。
  * `colstat::Union{Nothing,AbstractVector{Int32}}`: 制約行列の列の基準ステータスを保持するための長さ ORIGINALCOLS の整数配列。

C API の対応する関数 [XPRSgetbasis](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetbasis.html) のドキュメントも参照してください。
