```
reach(prop::FiniteTimeReachability)
```

Return the set of states with which to compute reachbility for a finite time reachability prop. This is equivalent for [`terminal_states(prop::FiniteTimeReachability)`](@ref) for a regular reachability property. See [`FiniteTimeReachAvoid`](@ref) for a more complex property where the reachability and terminal states differ.
