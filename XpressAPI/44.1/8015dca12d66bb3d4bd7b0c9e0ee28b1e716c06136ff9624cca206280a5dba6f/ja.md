```
XPRSgetlpsolval(prob, col, row)::x, slack, dual, dj
```

**非推奨** XPRSgetsolution または XPRSgetcallbacksolution および関連する関数を使用してください。

最適化後に単一の LP ソリューション値を取得するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `col::Integer`: ソリューション値を返す変数の列インデックス。
  * `row::Integer`: ソリューション値を返す制約の行インデックス。

# 戻り値

  * `x::Float64`: プライマル変数の値が返されるダブルポインタ。
  * `slack::Float64`: スラック変数の値が返されるダブルポインタ。
  * `dual::Float64`: デュアル変数の値 (cBTB-1) が返されるダブルポインタ。
  * `dj::Float64`: 変数の削減コスト (cT-cBTB-1A) が返されるダブルポインタ。

C API の対応する関数 [XPRSgetlpsolval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetlpsolval.html) のドキュメントも参照してください。
