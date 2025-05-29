```
Base.numerator(a::FunctionFieldElem{T}, canonicalise::Bool=true) where T <: FieldElement
Base.denominator(a::FunctionFieldElem{T}, canonicalise::Bool=true) where T <: FieldElement
```

関数体要素 `a` の分子と分母を返します。要素は分数自由形式で保存されているため、分母は要素 `a` の係数の共通分母です。`canonicalise` が `true` に設定されている場合、分数は最初に正準化されます。
