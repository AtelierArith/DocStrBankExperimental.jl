```
Base.numerator(a::FunctionFieldElem{T}, canonicalise::Bool=true) where T <: FieldElement
Base.denominator(a::FunctionFieldElem{T}, canonicalise::Bool=true) where T <: FieldElement
```

Return the numerator and denominator of the function field element `a`. Note that elements are stored in fraction free form so that the denominator is a common denominator for the coefficients of the element `a`. If `canonicalise` is set to `true` the fraction is first canonicalised.
