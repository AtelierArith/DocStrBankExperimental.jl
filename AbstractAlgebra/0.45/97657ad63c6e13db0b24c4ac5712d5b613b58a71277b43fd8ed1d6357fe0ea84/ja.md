```
+(x::MatrixElem{T}, y::T) where {T <: RingElem}
```

$$
x + S(y)
$$

を返します。ここで、$S$は$x$の親です。
