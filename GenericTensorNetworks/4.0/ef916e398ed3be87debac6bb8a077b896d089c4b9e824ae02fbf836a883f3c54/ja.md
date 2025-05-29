```
CountingMax{K} <: AbstractProperty
CountingMax(K=Single)
```

最大-Kサイズのセットの数をカウントします。例えば、[`IndependentSet`](@ref)問題の場合、独立したサイズのセットをカウントします $\alpha(G), \alpha(G)-1, \ldots, \alpha(G)-K+1$。

  * 対応するテンソル要素タイプは、`K`が`Single`の場合は[`CountingTropical`](@ref)、`K`が整数の場合は[`TruncatedPoly`](@ref)`{K}`です。
  * 重み付き制約充足問題は、`K`が`Single`の場合のみサポートされています。
  * GPUはサポートされています、
