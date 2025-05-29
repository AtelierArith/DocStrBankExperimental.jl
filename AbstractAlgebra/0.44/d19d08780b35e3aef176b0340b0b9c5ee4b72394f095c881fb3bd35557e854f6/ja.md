```
-(x::Union{Integer, Rational, AbstractFloat}, y::MatrixElem{T}) where T <: NCRingElement
```

$$
S(x) - y
$$

を返します。ここで、$S$ は $y$ の親です。
