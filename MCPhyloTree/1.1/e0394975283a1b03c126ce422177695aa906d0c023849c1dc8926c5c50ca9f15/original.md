```
majority_consensus_tree(trees::Vector{T}, percentage::Float64=0.5)
    ::T where T<:AbstractNode
```

Construct the majority rule consensus tree from a set of trees that share the same leafset. By default the output tree includes clusters that occur in over 50% of the trees. This can be customized when calling the function. The function returns the root node of the majority consensus tree, from which it can be traversed. The algorithm is based on section 3 and 6.1 of:

Jesper Jansson, Chuanqi Shen, and Wing-Kin Sung. 2016. Improved algorithms for constructing consensustrees. J. ACM 63, 3, Article 28 (June 2016), 24 pages https://dl.acm.org/doi/pdf/10.1145/2925985
