```
loose_consensus_tree(trees::Vector{T})::T where T<:AbstractNode
```

Construct the loose consensus tree from a set of trees that share the same leafset. I.e. a tree with all the clusters that appear in at least one tree and are compatible with all trees. Returns the root node of the loose consensus tree, from which it can be traversed. This algorithm is based on section 4 and 6.1 of:

Jesper Jansson, Chuanqi Shen, and Wing-Kin Sung. 2016. Improved algorithms for constructing consensustrees. J. ACM 63, 3, Article 28 (June 2016), 24 pages https://dl.acm.org/doi/pdf/10.1145/2925985
