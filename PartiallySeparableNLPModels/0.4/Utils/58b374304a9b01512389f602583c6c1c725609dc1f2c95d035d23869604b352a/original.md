```
partitioned_structure = build_PartitionedDataTRPQN(expr_tree, n)
```

Return the structure required to run a partitioned quasi-Newton trust-region method.  It finds the partially-separable structure of an expression tree `expr_tree` representing f(x) = ∑fᵢ(xᵢ). Then it allocates the partitioned structures required. To define properly the sparse matrix of the partitioned matrix we need the size of the problem: `n`.
