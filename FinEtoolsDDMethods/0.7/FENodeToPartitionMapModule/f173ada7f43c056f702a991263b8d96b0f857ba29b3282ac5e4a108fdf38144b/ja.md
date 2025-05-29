```
FENodeToPartitionMap(n2e::N2EMAP, element_partitioning::Vector{IT}) where {N2EMAP<:FENodeToFEMap,N,IT<:Integer}
```

有限要素ノードからそれらが属するパーティションへのマッピング。

# 引数

  * `n2e::N2EMAP`: 有限要素ノードと有限要素の間のマッピング。
  * `element_partitioning::Vector{IT}`: 要素のパーティショニングを指定するベクター。
