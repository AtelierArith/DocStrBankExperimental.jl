```
UniformHole <: AbstractHole
```

  * `domain`: A bitvector, where the `i`th bit is set to true if the `i`th rule in the grammar can be applied. All rules in the domain are required to have the same childtypes.
  * `children`: The children of this hole in the expression tree.
