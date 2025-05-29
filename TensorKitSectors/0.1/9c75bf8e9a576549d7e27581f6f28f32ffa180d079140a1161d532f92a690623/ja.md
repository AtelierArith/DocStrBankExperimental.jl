```
⊗(a::I, b::I...) where {I<:Sector}
otimes(a::I, b::I...) where {I<:Sector}
```

`a ⊗ b`の融合積に現れる`c::I`の要素のイテラブルを返します。

すべての要素`c`は最大1回しか現れないことに注意してください。融合の重複（`FusionStyle(I) == GenericFusion()`の場合）は、`Nsymbol(a, b, c)`を介してアクセスする必要があります。
