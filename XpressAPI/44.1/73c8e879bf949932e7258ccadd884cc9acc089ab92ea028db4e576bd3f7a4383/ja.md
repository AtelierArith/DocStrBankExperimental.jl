```
XPRSloadmodelcuts(prob, nrows, rowind)::prob
```

行列のセットがモデルカットとして扱われることを指定します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: モデルカットの数。
  * `rowind::AbstractVector{Integer}`: カットとして扱われる行インデックスの配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSloadmodelcuts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmodelcuts.html)のドキュメントも参照してください。
