```
is_integral_model(E::EllipticCurve{T}) -> Bool where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

Given an elliptic curve $E$ over QQ or a number field $K$, return true if $E$ is an integral model of $E$.
