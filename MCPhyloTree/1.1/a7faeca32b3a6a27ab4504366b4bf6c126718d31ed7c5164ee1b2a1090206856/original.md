```
greedy_consensus_tree(trees::Vector{T})::T where T<:AbstractNode
```

Construct the greedy consensus tree from a set of trees that share the same leafset.  Returns the root node of the greedy consensus tree, from which it can be traversed. This algorithm is based on section 5 and 6.1 of:

Jesper Jansson, Chuanqi Shen, and Wing-Kin Sung. 2016. Improved algorithms for constructing consensustrees. J. ACM 63, 3, Article 28 (June 2016), 24 pages https://dl.acm.org/doi/pdf/10.1145/2925985
