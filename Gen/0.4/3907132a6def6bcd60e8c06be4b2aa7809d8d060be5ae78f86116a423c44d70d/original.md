```
abstract type HierarchicalSelection <: Selection end
```

Abstract type for selections that have a notion of sub-selections.

```
get_subselections(selection::HierarchicalSelection)
```

Return an iterator over pairs of addresses and subselections at associated addresses.
