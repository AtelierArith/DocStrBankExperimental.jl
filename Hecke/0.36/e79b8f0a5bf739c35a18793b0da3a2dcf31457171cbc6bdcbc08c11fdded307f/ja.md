```
abs_upper_bound(::Type{ZZRingElem}, x::ArbFieldElem) -> ZZRingElem
```

正の整数 $b$ を返します。型は `ZZRingElem` であり、$\lvert x \rvert \leq b$ です。$b$ が可能な限り厳密であることは保証されていません。
