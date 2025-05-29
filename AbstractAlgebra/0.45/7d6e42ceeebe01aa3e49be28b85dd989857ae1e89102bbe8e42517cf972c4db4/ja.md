```
coefficients(a::MPolyRingElem{T}) where T <: RingElement
```

与えられた多項式の係数のイテレータを返します。係数の配列を取得するには、`collect(coefficients(a))`を使用してください。
