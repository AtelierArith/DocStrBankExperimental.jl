```
CountingMin{K} <: AbstractProperty
CountingMin(K=Single)
```

最小-Kサイズのセットの数をカウントします。

  * 対応するテンソル要素タイプは、`K`が`Single`の場合は逆の[`CountingTropical`](@ref)であり、`K`が整数の場合は[`TruncatedPoly`](@ref)`{K}`です。
  * 重み付き制約充足問題は、`K`が`Single`の場合のみサポートされています。
  * GPUがサポートされています。
