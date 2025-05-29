```
tensor(a::WaveguideOperatorT, b::Operator{BL,BR,F}) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
tensor(a::Operator{BL,BR,F}, b::WaveguideOperatorT) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
tensor(a::WaveguideOperator, b::Operator{BL,BR,F}) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
tensor(a::Operator{BL,BR,F}, b::WaveguideOperator) where {BL<:NLevelBasis,BR<:NLevelBasis,F}
```

Nレベル基底演算子のための特化したテンソル積メソッド。
