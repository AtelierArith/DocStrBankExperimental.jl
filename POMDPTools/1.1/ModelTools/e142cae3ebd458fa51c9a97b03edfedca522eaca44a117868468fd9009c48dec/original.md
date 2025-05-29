```
transition_matrices(m::Union{MDP,POMDP})
transition_matrices(m; sparse=true)
```

Construct transition matrices for (PO)MDP m.

The returned object is an associative object (usually a Dict), where the keys are actions. Each value in this object is an AbstractMatrix where the row corresponds to the state index of s and the column corresponds to the state index of s'. The entry in the matrix is the probability of transitioning from state s to state s'.
