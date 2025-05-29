```
RF(tree1::T, tree2::T)::Int64 where T <:AbstractNode
```

Calculate the Robinson-Foulds distance between the two trees. In its current form the function assumes the trees have identical leave sets.

Returns result of algorithm as integer.

  * `tree1` : tree used to determine RF distance.
  * `tree2` : tree used to determine RF distance.
