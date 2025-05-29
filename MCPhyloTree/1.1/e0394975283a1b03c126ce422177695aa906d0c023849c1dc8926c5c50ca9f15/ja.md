```
majority_consensus_tree(trees::Vector{T}, percentage::Float64=0.5)
    ::T where T<:AbstractNode
```

同じ葉集合を共有する木のセットから多数決ルールのコンセンサスツリーを構築します。デフォルトでは、出力ツリーには50%以上の木に出現するクラスタが含まれます。これは関数を呼び出す際にカスタマイズできます。この関数は多数決コンセンサスツリーの根ノードを返し、そこから木を遍歴できます。このアルゴリズムは以下の文献のセクション3および6.1に基づいています：

Jesper Jansson, Chuanqi Shen, and Wing-Kin Sung. 2016. Improved algorithms for constructing consensustrees. J. ACM 63, 3, Article 28 (June 2016), 24 pages https://dl.acm.org/doi/pdf/10.1145/2925985
