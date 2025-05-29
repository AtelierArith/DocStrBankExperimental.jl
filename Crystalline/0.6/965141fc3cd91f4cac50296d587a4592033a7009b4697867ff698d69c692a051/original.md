```
issymmorph(sgnum::Integer, D::Integer=3) --> Bool
```

Return whether the space group with number `sgnum` and dimensionality `D` is symmorphic  (`true`) or nonsymmorphic (`false`).

Equivalent to `issymmorph(spacegroup(sgnum, D))` but uses memoization for performance.
