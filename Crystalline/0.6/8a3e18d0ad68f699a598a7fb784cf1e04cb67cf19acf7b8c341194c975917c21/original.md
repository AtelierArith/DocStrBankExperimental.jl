```
issymmorph(op::SymOperation, cntr::Char) --> Bool
```

Return whether a given symmetry operation `op` is symmorphic (`true`) or nonsymmorphic (`false`). 

The operation is assumed provided in conventional basis with centering type `cntr`:  checking symmorphism is then equivalent to checking whether the operation's translation part is zero or a lattice vector in the associated primitive basis.
