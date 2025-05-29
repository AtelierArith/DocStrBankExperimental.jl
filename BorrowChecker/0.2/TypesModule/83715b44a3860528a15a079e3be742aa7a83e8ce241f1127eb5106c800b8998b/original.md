```
BorrowedMut{T,O<:OwnedMut} <: AbstractBorrowed{T}
```

A mutable reference to an owned value. Common operations:

  * Create using `@ref lt :mut x = value`
  * Access value using `@take` (copies)
  * Access fields/indices via `.field` or `[indices...]` (returns LazyAccessor)

Only one mutable reference can exist at a time, and no immutable references can exist simultaneously.

# Internal fields (not part of public API):

  * `value::T`: The referenced value
  * `owner::O`: The original owned value
  * `lifetime::Lifetime`: The scope in which this reference is valid
  * `symbol::Symbol`: Variable name for error reporting
