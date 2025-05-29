```
roots(Q::QadicField, f::ZZPolyRingElem; max_roots::Int = degree(f)) -> Vector{QadicFieldElem}
```

$$
Q
$$

における$f$の根、$f$は平方フリーでなければならない（少なくとも根は単純根でなければならない）。
