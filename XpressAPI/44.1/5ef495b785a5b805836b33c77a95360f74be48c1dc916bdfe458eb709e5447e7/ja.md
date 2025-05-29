```
XPRSclearrowflags(prob, flags, first, last)::prob
```

行の範囲に付随する余分な情報をクリアします。

# 引数

  * `prob::XPRSprob`: 現在の問題
  * `flags::AbstractVector{Integer}`: 削除する余分な情報のタイプを含む長さ `last-first+1` の整数配列（下記参照）
  * `first::Integer`: チェックする最初の行インデックス
  * `last::Integer`: チェックする最後の行インデックス

# 戻り値

  * `prob::XPRSprob`: 現在の問題

C APIの対応する関数 [XPRSclearrowflags](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSclearrowflags.html) のドキュメントも参照してください。
