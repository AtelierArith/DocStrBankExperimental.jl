```
induce_crt(a::Generic.Poly{AbsSimpleNumFieldElem}, p::ZZRingElem, b::Generic.Poly{AbsSimpleNumFieldElem}, q::ZZRingElem) -> Generic.Poly{AbsSimpleNumFieldElem}, ZZRingElem
```

Given polynomials $a$ defined modulo $p$ and $b$ modulo $q$, apply the CRT to all coefficients recursively. Implicitly assumes that $a$ and $b$ have integral coefficients (i.e. no denominators).
