```
induce_crt(a::Generic.Poly{AbsSimpleNumFieldElem}, p::ZZRingElem, b::Generic.Poly{AbsSimpleNumFieldElem}, q::ZZRingElem) -> Generic.Poly{AbsSimpleNumFieldElem}, ZZRingElem
```

多項式 $a$ が $p$ で定義され、$b$ が $q$ で定義されている場合、すべての係数に対して CRT を再帰的に適用します。暗黙的に $a$ と $b$ が整数係数を持つ（すなわち、分母がない）ことを前提としています。
