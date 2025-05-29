```
XPRS_bo_addcuts(bo, branch, ncuts, cutind)::Nothing
```

ユーザーが保存したカットをユーザー分岐オブジェクトのブランチに新しい制約として追加します。

# 引数

  * `bo::XPRSbranchobject`: 修正するユーザー分岐オブジェクト。
  * `branch::Integer`: カットを追加するブランチの番号。
  * `ncuts::Integer`: 追加するカットの数。
  * `cutind::AbstractVector{Ptr{Cvoid}}`: ブランチに追加すべきユーザーカットへのポインタを含む長さ `ncuts` の配列。

C APIの対応する関数 [XPRS*bo*addcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_addcuts.html) のドキュメントも参照してください。
