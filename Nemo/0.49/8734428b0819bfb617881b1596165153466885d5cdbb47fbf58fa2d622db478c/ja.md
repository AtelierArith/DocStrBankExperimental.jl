```
primorial(x::ZZRingElem)
```

$$
x
$$

以下のすべての素数の積、すなわち$x$のプライモリアルを返します。もし$x < 0$の場合は、`DomainError()`をスローします。
