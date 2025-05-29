```
Base.numerator(R::FunctionField{T}, canonicalise::Bool=true) where T <: FieldElement
Base.denominator(R::FunctionField{T}, canonicalise::Bool=true) where T <: FieldElement
```

Thinking of elements of the rational function field as fractions, put the defining polynomial of the function field over a common denominator and return the numerator/denominator respectively. Note that the resulting polynomials belong to a different ring than the original defining polynomial. The `canonicalise` is ignored, but exists for compatibility with the Generic interface.
