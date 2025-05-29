```
XPRSgetcutmap(prob, ncuts, cutind, cutmap)::cutmap
```

現在、最適化プログラムに読み込まれているカットのリストがどの行にあるかを返すために使用されます。

これは、アクティブなカットに関連する双対を取得するために便利です。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncuts::Integer`: cutind 配列内のカットの数。
  * `cutind::AbstractVector{Ptr{Cvoid}}`: 行インデックスが要求されるカットへのポインタ配列。
  * `cutmap::Union{XPRSallocatable,AbstractVector{Int32}}`: 行インデックスが返される長さ `ncuts` の整数配列。この引数には `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てることができます。

# 戻り値

  * `cutmap::AbstractVector{Int32}`: 行インデックスが返される長さ `ncuts` の整数配列。

C API の対応する関数 [XPRSgetcutmap](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcutmap.html) のドキュメントも参照してください。
