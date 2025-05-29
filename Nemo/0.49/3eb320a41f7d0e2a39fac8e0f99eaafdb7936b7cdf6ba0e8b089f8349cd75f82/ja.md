```
moebius_mu(x::ZZRingElem)
```

$$
x
$$

のMoebius mu関数を`Int`として返します。返される値は$-1$、$0$、または$1$のいずれかです。$x \leq 0$の場合は`DomainError()`をスローします。
