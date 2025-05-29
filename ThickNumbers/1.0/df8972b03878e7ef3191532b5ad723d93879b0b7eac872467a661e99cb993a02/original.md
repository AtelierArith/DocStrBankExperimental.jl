```
isapprox_tn(a::ThickNumber, b::ThickNumber; atol=0, rtol::Real=atol>0 ? 0 : √eps)
a ⩪ b (`\dotsim`-TAB)
```

Returns `true` if `a` and `b` are both empty or both `loval` and `hival` are approximately equal (≈). It is `false` otherwise.
