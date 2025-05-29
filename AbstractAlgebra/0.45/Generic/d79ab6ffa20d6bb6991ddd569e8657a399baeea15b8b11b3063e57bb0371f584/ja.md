```
exponent_word(a::FreeAssociativeAlgebraElem{T}, i::Int) where T <: RingElement
```

$ a $ の $ i $ 番目の項の単項式に対応する変数インデックスのベクトルを返します。項の番号は $ 1 $ から始まり、変数インデックスは環の変数の順序で与えられます。
