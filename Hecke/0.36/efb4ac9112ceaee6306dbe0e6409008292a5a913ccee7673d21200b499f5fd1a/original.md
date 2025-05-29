```
in(a::Generic.RationalFunctionFieldElem{T}, R::KInftyRing{T}) where T <: FieldElement
```

Return `true` if the given element of the rational function field is an element of $k_\infty(x)$, i.e. if `degree(numerator) <= degree(denominator)`.
