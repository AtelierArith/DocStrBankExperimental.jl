```
actiontype(t::Type)
actiontype(p::Union{POMDP,MDP})
```

Return the state type for a problem type (the `S` in `POMDP{S,A,O}`).

```
type A <: POMDP{Bool, Int, Bool} end

actiontype(A) # returns Int
```
