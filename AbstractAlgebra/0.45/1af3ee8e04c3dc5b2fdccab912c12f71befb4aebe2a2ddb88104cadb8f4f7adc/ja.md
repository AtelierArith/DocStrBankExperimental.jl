```
derivative(f::MPolyRingElem{T}, x::MPolyRingElem{T}) where T <: RingElement
```

`f`に関する`x`の偏微分を返します。値`x`は`f`の多項式環の生成元でなければなりません。
