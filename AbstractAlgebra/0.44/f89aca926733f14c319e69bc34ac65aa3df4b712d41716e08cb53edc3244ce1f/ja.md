```
pseudodivrem(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: RingElement
```

$$
g
$$

で割ったときの擬似商と擬似余りからなるタプル$(q, r)$を返します。もし$g = 0$の場合は`DivideError()`をスローします。
