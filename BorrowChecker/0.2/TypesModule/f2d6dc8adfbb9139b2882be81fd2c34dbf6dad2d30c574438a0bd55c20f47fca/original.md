```
Owned{T} <: AbstractOwned{T}
```

An immutable owned value. Common operations:

  * Create using `@own x = value`
  * Access value using `@take!` (moves) or `@take` (copies)
  * Borrow using `@ref`
  * Access fields/indices via `.field` or `[indices...]` (returns LazyAccessor)

Once moved, the value cannot be accessed again.

# Internal fields (not part of public API):

  * `value::T`: The contained value
  * `moved::Bool`: Whether the value has been moved
  * `immutable_borrows::Int`: Count of active immutable borrows
  * `symbol::Symbol`: Variable name for error reporting
