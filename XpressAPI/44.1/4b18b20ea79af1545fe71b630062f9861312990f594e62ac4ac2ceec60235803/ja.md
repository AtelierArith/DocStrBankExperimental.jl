```
XPRSgetrowflags(prob, flags, first, last)::flags
```

特定の行が特別な行として設定されているかどうかを取得します。

# 引数

  * `prob::XPRSprob`: 現在の問題
  * `flags::Union{XPRSallocatable,AbstractVector{Int32}}`: 情報のタイプが返される長さ `last-first+1` の整数配列。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。
  * `first::Integer`: チェックする最初の行インデックス
  * `last::Integer`: チェックする最後の行インデックス

# 戻り値

  * `flags::AbstractVector{Int32}`: 情報のタイプが返される長さ `last-first+1` の整数配列

C APIの対応する関数 [XPRSgetrowflags](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrowflags.html) のドキュメントも参照してください。
