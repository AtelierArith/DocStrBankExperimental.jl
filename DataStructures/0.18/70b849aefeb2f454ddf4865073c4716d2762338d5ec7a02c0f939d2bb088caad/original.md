```
compare(m::SAContainer, s::IntSemiToken, t::IntSemiToken)
```

Determines the  relative positions of the  data items indexed by `(m,s)` and  `(m,t)` in the sorted order. The  return value is `-1` if `(m,s)` precedes `(m,t)`, `0` if they are equal, and `1` if `(m,s)` succeeds `(m,t)`. `s`  and `t`  are semitokens  for the  same container `m`.
