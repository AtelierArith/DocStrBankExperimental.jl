```
+(x::MatrixElem{T}, y::Union{Integer, Rational, AbstractFloat}) where T <: NCRingElement
```

$$
x + S(y)
$$

を返します。ここで、$S$ は $x$ の親です。
