```
rem_relation!(p::Poset, a::Integer, b::Integer)::Bool
```

Delete the relation `a < b` from the poset `p` as well as all  relations of the form `a < x` and `x < b` where `x` is between `a` and `b`.
