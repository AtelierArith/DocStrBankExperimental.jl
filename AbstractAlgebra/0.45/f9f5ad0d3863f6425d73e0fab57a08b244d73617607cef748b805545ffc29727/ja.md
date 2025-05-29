```
==(x::Union{Integer, Rational, AbstractFloat}, y::MatrixElem{T}) where T <: NCRingElement
```

$$
S(x) == y
$$

の場合は `true` を返し、そうでなければ `false` を返します。ここで、$S$ は $y$ の親です。
