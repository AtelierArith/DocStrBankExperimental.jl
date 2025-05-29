```julia
abstract type NodePatchGroups <: ExtendableGrids.AbstractGridIntegerArray1D
```

Vector with patch groups for nodes (ensuring that node patches of nodes in same group do not overlap)
