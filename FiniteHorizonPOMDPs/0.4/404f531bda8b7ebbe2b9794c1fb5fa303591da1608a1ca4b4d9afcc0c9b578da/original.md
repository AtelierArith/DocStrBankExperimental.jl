```
fixhorizon(m::Union{MDP,POMDP}, horizon::Int)
```

Wrap infinite horizon (PO)MDP `m` and `horizon` to the new structure creating Finite Horizon (PO)MDP.
