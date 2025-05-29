```
rising_factorial(x::ZZRingElem, n::ZZRingElem)
```

$ x $ の上昇階乗を返します。すなわち、$ x(x + 1)(x + 2)\cdots (x + n - 1) $ です。もし $ n < 0 $ の場合は `DomainError()` をスローします。
