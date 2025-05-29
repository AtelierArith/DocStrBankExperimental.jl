```
distance(t::Tree, n1::AbstractString, n2::AbstractString; topological=false)
distance(n1::TreeNode, n2::TreeNode; topological=false)
```

Compute branch length distance between `n1` and `n2` by summing the `branch_length` values. If `topological`, the value `1.` is summed instead, counting the number of branches separating the two nodes (*Note*: the output is not an `Int`!).
