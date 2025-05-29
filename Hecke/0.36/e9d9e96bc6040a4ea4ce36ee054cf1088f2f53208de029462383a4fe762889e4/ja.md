```
factor(a::AbsSimpleNumFieldOrderElem) -> Fac{AbsSimpleNumFieldOrderElem}
```

$ a $ の不可約要素への因数分解を計算します。返り値は因数分解 `fac` であり、これは `a = unit(fac) * prod(p^e for (p, e) in fac)` を満たします。

この関数は、$ a $ がゼロでないことと、$ a $ を含むすべての素イデアルが主イデアルであることを要求します。これは、例えば $ a $ の整域の類群が自明である場合に満たされます。
