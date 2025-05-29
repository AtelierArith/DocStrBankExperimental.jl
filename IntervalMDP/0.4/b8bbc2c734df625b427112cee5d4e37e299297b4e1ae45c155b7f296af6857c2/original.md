```
reach(prop::InfiniteTimeReachability)
```

Return the set of states with which to compute reachbility for a infinite time reachability property. This is equivalent for [`terminal_states(prop::InfiniteTimeReachability)`](@ref) for a regular reachability property. See [`InfiniteTimeReachAvoid`](@ref) for a more complex property where the reachability and terminal states differ.
