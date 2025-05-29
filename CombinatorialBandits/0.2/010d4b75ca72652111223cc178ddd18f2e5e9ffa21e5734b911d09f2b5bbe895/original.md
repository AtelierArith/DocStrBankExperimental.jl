```
is_partially_acceptable(instance::CombinatorialInstance{T}, arms::Vector{T})
```

Returns whether the set of arms is either a solution or the subset of a solution that can be played for the given combinatorial instance. In some cases, a subset of a solution is not a solution: the distinction between the two states is made by calling `is_feasible`.

Typically, `is_partially_acceptable` returns `true` for an empty set of arms: even if this is not an acceptable solution, adding elements to the empty set may yield a perfectly acceptable solution.
