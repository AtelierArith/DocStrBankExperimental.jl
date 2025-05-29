```
==(x::MatrixElem{T}, y::T) where {T <: NCRingElem}
```

$$
S(y)
$$

が$x$の親である場合、$x == S(y)$が算術的に成り立つなら`true`を返し、それ以外の場合は`false`を返します。
