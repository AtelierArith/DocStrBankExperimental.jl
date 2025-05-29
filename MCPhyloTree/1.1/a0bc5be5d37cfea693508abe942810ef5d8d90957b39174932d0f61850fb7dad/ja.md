```
loose_consensus_tree(trees::Vector{T})::T where T<:AbstractNode
```

同じ葉集合を共有する木のセットからルーズコンセンサスツリーを構築します。すなわち、少なくとも1つの木に現れ、すべての木と互換性のあるすべてのクラスターを持つ木です。ルーズコンセンサスツリーの根ノードを返し、そこから木を遍歴できます。このアルゴリズムは、次の文献のセクション4および6.1に基づいています。

Jesper Jansson, Chuanqi Shen, and Wing-Kin Sung. 2016. Improved algorithms for constructing consensustrees. J. ACM 63, 3, Article 28 (June 2016), 24 pages https://dl.acm.org/doi/pdf/10.1145/2925985
