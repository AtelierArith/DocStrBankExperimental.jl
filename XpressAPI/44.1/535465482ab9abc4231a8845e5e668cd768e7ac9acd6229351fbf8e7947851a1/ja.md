```
XPRSdelsets(prob, nsets, setind)::prob
```

問題からセットを削除します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nsets::Integer`: 削除するセットの数。
  * `setind::AbstractVector{Integer}`: 削除するセットを含む長さ `nsets` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSdelsets](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelsets.html)のドキュメントも参照してください。
