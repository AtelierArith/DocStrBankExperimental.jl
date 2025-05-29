```
tensor(a::WaveguideOperatorT, b::Operator{BL,BR,F}) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
tensor(a::Operator{BL,BR,F}, b::WaveguideOperatorT) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
tensor(a::WaveguideOperator, b::Operator{BL,BR,F}) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
tensor(a::Operator{BL,BR,F}, b::WaveguideOperator) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
```

Specialized tensor product methods for N-level basis operators.
