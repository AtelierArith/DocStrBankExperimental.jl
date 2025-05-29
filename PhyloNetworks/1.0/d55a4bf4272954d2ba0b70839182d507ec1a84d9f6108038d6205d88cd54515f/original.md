```
istimeconsistent(net, checkpreorder::Bool=true)
```

True (resp. false) if `net` network is (resp. is not) time-consistent. A network is time-consistent if for any node `v`, all paths from the root to `v` have the same length. It is sufficient to check this condition at nodes `v` that are hybrid nodes.

See also [`getnodeheights`](@ref) and [`getnodeheights_average`](@ref).
