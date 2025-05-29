```
pseudorem(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: RingElement
```

$$
g
$$

で割ったときの$f$の擬似余りを返します。もし$g = 0$の場合は、`DivideError()`をスローします。
