```
monomials(a::MPolyRingElem{T}) where T <: RingElement
```

与えられた多項式の単項式のイテレータを返します。単項式の配列を取得するには、`collect(monomials(a))`を使用してください。
