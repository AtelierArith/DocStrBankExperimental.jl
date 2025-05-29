```
dot(y::PDVec, A::AbstractObservable, x::PDVec[, w::PDWorkingMemory])
```

Perform `y ⋅ A ⋅ x`. The working memory `w` is required to facilitate threaded/distributed operations with non-diagonal `A`. If needed and not passed a new instance will be allocated. `A` can be replaced with a tuple of operators.

See [`PDVec`](@ref), [`PDWorkingMemory`](@ref).
