```
==(x::T, y::MatrixElem{T}) where {T <: NCRingElem}
```

$$
S(x) == y
$$

の場合は `true` を返し、そうでなければ `false` を返します。ここで、$S$ は $y$ の親です。
