```
roots(Q::QadicField, f::ZZPolyRingElem; max_roots::Int = degree(f)) -> Vector{QadicFieldElem}
```

$$
f
$$

の $Q$ における根、$f$ は平方フリーでなければならない（少なくとも根は単純根でなければならない）。
