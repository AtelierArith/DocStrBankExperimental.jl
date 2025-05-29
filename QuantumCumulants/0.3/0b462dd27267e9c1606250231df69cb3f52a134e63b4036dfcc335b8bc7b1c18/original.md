```
NumberedOperator <: QSym
```

Defines an operator, associated with a Number. Commutator-relations are calculated using these numbers, as a sort of a specific index-value.

# Fields:

  * op: An Operator, either a [`Transition`](@ref), a [`Destroy`](@ref) or a [`Create`](@ref) can be defined.
  * numb: An Integer Number.
