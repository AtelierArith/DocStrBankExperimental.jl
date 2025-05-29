```
are_incomparable(p::Poset, a::Integer, b::Integer)::Bool
```

Returns `true` provided both `a` and `b` are in `p` and none of the following are true: `a<b` or `a==b` or `b<a`.
