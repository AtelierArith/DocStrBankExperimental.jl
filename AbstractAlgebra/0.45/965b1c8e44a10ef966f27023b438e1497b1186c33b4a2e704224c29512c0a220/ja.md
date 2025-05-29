```
exponent_vectors(a::MPolyRingElem{T}) where T <: RingElement
```

与えられた多項式の指数ベクトルのイテレータを返します。指数ベクトルの配列を取得するには、`collect(exponent_vectors(a))`を使用してください。
