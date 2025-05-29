```
statetype(t::Type)
statetype(p::Union{POMDP,MDP})
```

Return the state type for a problem type (the `S` in `POMDP{S,A,O}`).

```
type A <: POMDP{Int, Bool, Bool} end

statetype(A) # returns Int
```
