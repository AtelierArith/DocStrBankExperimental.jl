```
tensor(a::AbstractOperator, b::Bra)
tensor(a::Bra, b::AbstractOperator)
tensor(a::AbstractOperator, b::Ket)
tensor(a::Ket, b::AbstractOperator)
```

Products of operators and state vectors $a ⊗ <b|$. The result is an isometry in case the operator is unitary and state is normalized.
