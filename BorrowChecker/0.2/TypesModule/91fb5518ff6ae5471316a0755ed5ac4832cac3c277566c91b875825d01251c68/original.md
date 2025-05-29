```
OwnedMut{T} <: AbstractOwned{T}
```

A mutable owned value. Common operations:

  * Create using `@own :mut x = value`
  * Access value using `@take!` (moves) or `@take` (copies)
  * Modify by setproperty! or setindex!: `x.field = value` or `x[indices...] = value`
  * Borrow using `@ref` or `@ref :mut`
  * Access fields/indices via `.field` or `[indices...]` (returns LazyAccessor)

Once moved, the value cannot be accessed again.

# Internal fields (not part of public API):

  * `value::T`: The contained value
  * `moved::Bool`: Whether the value has been moved
  * `immutable_borrows::Int`: Count of active immutable borrows
  * `mutable_borrows::Int`: Count of active mutable borrows
  * `symbol::Symbol`: Variable name for error reporting
