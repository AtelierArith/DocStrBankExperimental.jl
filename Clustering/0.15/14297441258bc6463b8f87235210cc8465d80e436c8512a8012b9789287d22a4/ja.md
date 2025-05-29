```
randindex(a, b) -> NTuple{4, Float64}
```

クラスタリング `c1` と `c2` の間のランダム関連指標のタプルを計算します。

`a` と `b` は、[`ClusteringResult`](@ref) インスタンスまたは割り当てベクトル (`AbstractVector{<:Integer}`) のいずれかです。

インデックスのタプルを返します：

  * Hubert & Arabie 調整ランダムインデックス
  * ランダムインデックス（合意確率）
  * Mirkin のインデックス（不一致確率）
  * Hubert のインデックス ($P(\mathrm{agree}) - P(\mathrm{disagree})$)

# 参考文献

> Lawrence Hubert and Phipps Arabie (1985). *Comparing partitions.* Journal of Classification 2 (1): 193-218


> Meila, Marina (2003). *Comparing Clusterings by the Variation of Information.* Learning Theory and Kernel Machines: 173-187.


> Steinley, Douglas (2004). *Properties of the Hubert-Arabie Adjusted Rand Index.* Psychological Methods, Vol. 9, No. 3: 386-396

