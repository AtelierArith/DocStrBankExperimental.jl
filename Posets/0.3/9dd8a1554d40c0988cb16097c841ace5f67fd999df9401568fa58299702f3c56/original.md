```
iso(p::Poset, q::Poset)::Dict{Int,Int}
```

Find an isomorphism from poset `p` to poset `q`, or throw an error  if the posets are not isomorphic. A dictionary is returned mapping vertices of `p` to vertices of `q`.
