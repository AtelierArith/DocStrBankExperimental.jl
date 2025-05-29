```
mul!(y::PDVec, A::AbstractObservable, x::PDVec[, w::PDWorkingMemory])
```

Perform `y = A * x` in-place. The working memory `w` is required to facilitate threaded/distributed operations. If not passed a new instance will be allocated. `y` and `x` may be the same vector.

See [`PDVec`](@ref), [`PDWorkingMemory`](@ref), [`AbstractObservable`](@ref).
