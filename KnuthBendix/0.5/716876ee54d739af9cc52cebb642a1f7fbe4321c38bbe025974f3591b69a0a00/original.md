```
RewritingSystem{W<:AbstractWord, O<:Ordering}
RewritingSystem(rwrules::Vector{Pair{W,W}}, order[; confluent=false, reduced=false])
```

`RewritingSystem` holds the list of ordered (by `order`) rewriting rules of `W<:AbstractWord`s.
