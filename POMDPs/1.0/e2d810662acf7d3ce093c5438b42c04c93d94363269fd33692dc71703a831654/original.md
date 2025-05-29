```
obstype(t::Type)
```

Return the state type for a problem type (the `S` in `POMDP{S,A,O}`).

```
type A <: POMDP{Bool, Bool, Int} end

obstype(A) # returns Int
```
