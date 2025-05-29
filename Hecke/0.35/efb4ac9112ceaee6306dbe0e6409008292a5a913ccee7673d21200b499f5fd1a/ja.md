```
in(a::Generic.RationalFunctionFieldElem{T}, R::KInftyRing{T}) where T <: FieldElement
```

与えられた有理関数体の要素が $k_\infty(x)$ の要素である場合は `true` を返します。すなわち、`degree(numerator) <= degree(denominator)` である場合です。
