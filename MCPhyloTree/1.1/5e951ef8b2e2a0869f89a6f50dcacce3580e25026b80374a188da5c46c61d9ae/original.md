```
RF_weighted(tree1::T, tree2::T)::Float64 where T <:AbstractNode
```

Calculate the weighted Robinson-Foulds distance between the two trees. The raw Robinson-Foulds distance is weighted by the maximum distance between the trees. In its current form the function assumes the trees have identical leave sets.

Returns result of algorithm as integer.

  * `tree1` : tree used to determine RF distance.
  * `tree2` : tree used to determine RF distance.
