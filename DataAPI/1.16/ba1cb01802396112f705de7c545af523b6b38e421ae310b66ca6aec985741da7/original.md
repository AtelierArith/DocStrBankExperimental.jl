```
refpool(A)
```

Whenever available, return an indexable object `pool` such that, given the *original* array `A` and a "ref value" `x` taken from `refarray(A)`, `pool[x]` is the appropriate *original* value. Return `nothing` if such object is not available.

By default, `refpool(A)` returns `nothing`.

If `refpool(A)` is not `nothing`, then `refpool(A)[refarray(A)[I...]]` must be equal to (according to `isequal`) and of the same type as `A[I...]`, and the object returned by `refpool(A)` must implement the iteration and indexing interfaces as well as the `length`, `eachindex`, `keys`, `values`, `pairs`, `firstindex`, `lastindex`, and `eltype` functions in accordance with the `AbstractArray` interface.

This generic function is owned by DataAPI.jl itself, which is the sole provider of the default definition.
