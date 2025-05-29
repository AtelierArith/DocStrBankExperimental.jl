```
IndexedOperator <: QSym
IndexedOperator(op::Union{Transition,Create,Destroy},ind::Index)
```

Operator, associated with an index.

# Fields:

  * op: Operator, either a [`Transition`](@ref), a [`Destroy`](@ref) or a [`Create`](@ref) can be defined.
  * ind: The index, the operator will be associated with.
