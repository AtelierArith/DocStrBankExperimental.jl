```
abs_upper_bound(::Type{ZZRingElem}, x::ArbFieldElem) -> ZZRingElem
```

Returns a positive integer $b$ of type `ZZRingElem` such that $\lvert x \rvert \leq b$. It is not guaranteed that $b$ is as tight as possible.
