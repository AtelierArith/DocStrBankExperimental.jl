```
struct ComplementSelection <: Selection end
```

A hierarchical selection that is the complement of the given selection. An address is in the selection if it is not in the complement selection.
