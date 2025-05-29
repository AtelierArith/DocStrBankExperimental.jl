```
mutable struct TopDownIterator <: ProgramIterator
```

Enumerates a context-free grammar starting at [`Symbol`](@ref) `sym` with respect to the grammar up to a given depth and a given size.  The exploration is done using the given priority function for derivations, and the expand function for discovered nodes. Concrete iterators may overload the following methods:

  * priority_function
  * derivation_heuristic
  * hole_heuristic
