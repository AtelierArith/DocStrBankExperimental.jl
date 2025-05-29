```
exponent_words(a::FreeAssociativeAlgebraElem{T}) where T <: RingElement
```

与えられた多項式の指数単語のイテレータを返します。指数単語の配列を取得するには、`collect(exponent_words(a))`を使用します。
