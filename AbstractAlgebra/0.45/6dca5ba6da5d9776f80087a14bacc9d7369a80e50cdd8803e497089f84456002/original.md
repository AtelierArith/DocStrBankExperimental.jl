```
+(x::MatrixElem{T}, y::Union{Integer, Rational, AbstractFloat}) where T <: NCRingElement
```

Return $x + S(y)$ where $S$ is the parent of $x$.
