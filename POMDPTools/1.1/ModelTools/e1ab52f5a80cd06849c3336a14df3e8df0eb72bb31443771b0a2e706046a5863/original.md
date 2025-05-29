```
reward_vectors(m::Union{MDP, POMDP})
```

Construct reward vectors for (PO)MDP m.

The returned object is an associative object (usually a Dict), where the keys are actions. Each value in this object is an AbstractVector where the index corresponds to the state index of s and the entry is the reward for that state.
