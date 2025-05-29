```
conservationlaws(rs::ReactionSystem)
```

Return the conservation law matrix of the given `ReactionSystem`, calculating it if it is not already stored within the system, or returning an alias to it.

Notes:

  * The first time being called it is calculated and cached in `rn`, subsequent calls should be fast.
