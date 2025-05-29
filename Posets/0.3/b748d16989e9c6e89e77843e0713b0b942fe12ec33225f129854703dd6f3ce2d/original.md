```
add_relation!(p::Poset, a::Integer, b::Integer)::Bool
```

Add `a<b` as a relation in the poset. Returns `true` if successful.

This may also be invoked as follows:

  * `add_relation!(p, (a, b))`
  * `add_relation!(p, a => b)`
