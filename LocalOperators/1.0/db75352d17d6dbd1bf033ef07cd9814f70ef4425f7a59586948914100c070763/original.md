```
support(A::LocalOperator)
```

Returns the support of `A` as a `UnitRange` type. That is, returns the range of indices that the local operator `A` is defined on. Equivalent to `A.support` or `getfield(A, :support)`. See also [`maxsupport`](@ref) and [`minsupport`](@ref).
