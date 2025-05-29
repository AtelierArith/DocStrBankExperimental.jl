```
matching_map!(a₊, a₋, matcher; kw...) → rmap
```

Convenience function that first calls [`matching_map`](@ref) and then replaces the IDs in `a₊` with this `rmap`.
