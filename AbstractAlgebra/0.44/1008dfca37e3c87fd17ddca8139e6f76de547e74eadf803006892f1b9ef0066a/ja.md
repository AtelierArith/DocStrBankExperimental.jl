```
==(x::T, y::MatrixElem{T}) where {T <: NCRingElem}
```

$$
S(x) == y
$$

の場合は `true` を返し、そうでない場合は `false` を返します。ここで、$S$ は $y$ の親です。
