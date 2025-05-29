```
Base.numerator(R::FunctionField{T}, canonicalise::Bool=true) where T <: FieldElement
Base.denominator(R::FunctionField{T}, canonicalise::Bool=true) where T <: FieldElement
```

有理関数体の要素を分数として考え、関数体の定義多項式を共通分母の下に置き、それぞれ分子/分母を返します。結果として得られる多項式は、元の定義多項式とは異なる環に属することに注意してください。`canonicalise`は無視されますが、Genericインターフェースとの互換性のために存在します。
