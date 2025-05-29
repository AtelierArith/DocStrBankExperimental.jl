```
pseudorem(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: RingElement
```

$$
f
$$

を$g$で割ったときの擬似剰余を返します。もし$g = 0$の場合は、`DivideError()`をスローします。
