```
check(φ::Formula, i::Union{AbstractDict, AbstractVector}, args...)
```

Takes a [`Formula`](@ref) as input and returns its truth value in relation to the dictionary  or vector passed. We let any `AbstractDict` and `AbstractVector` be used as an interpretation  when model checking.

See also [`Formula`](@ref).
