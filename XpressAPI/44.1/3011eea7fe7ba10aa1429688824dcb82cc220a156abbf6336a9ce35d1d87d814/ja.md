```
XPRSslpdelcoefs(prob, ncoefs, rowind, colind)::prob
```

現在の問題から係数を削除します。

この関数の簡単なバージョンは XSLPdelformulas を参照してください。

# 引数

  * `prob::XPRSprob`: 現在の SLP 問題。
  * `ncoefs::Integer`: 削除する SLP 係数の数。
  * `rowind::AbstractVector{Integer}`: 削除する SLP 係数の行インデックス。
  * `colind::AbstractVector{Integer}`: 削除する SLP 係数の列インデックス。

# 戻り値

  * `prob::XPRSprob`: 現在の SLP 問題。

C API の対応する関数 [XPRSslpdelcoefs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpdelcoefs.html) のドキュメントも参照してください。
