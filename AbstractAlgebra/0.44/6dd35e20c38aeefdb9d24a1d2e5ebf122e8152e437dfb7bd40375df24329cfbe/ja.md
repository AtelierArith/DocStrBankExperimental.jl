```
==(x::MatrixElem{T}, y::Union{Integer, Rational, AbstractFloat}) where T <: NCRingElement
```

$$
S(y)
$$

が$x$の親であるとき、$x == S(y)$が算術的に成り立つ場合は`true`を返し、それ以外の場合は`false`を返します。
