```
Borrowed{T,O<:AbstractOwned} <: AbstractBorrowed{T}
```

An immutable reference to an owned value. Common operations:

  * Create using `@ref lt x = value`
  * Access value using `@take` (copies)
  * Access fields/indices via `.field` or `[indices...]` (returns LazyAccessor)

Multiple immutable references can exist simultaneously. The reference is valid only within its lifetime scope.

# Internal fields (not part of public API):

  * `value::T`: The referenced value
  * `owner::O`: The original owned value
  * `lifetime::Lifetime`: The scope in which this reference is valid
  * `symbol::Symbol`: Variable name for error reporting
