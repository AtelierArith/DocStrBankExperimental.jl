```
terms(a::MPolyRingElem{T}) where T <: RingElement
```

与えられた多項式の項のイテレータを返します。項の配列を取得するには、`collect(terms(a))`を使用してください。
