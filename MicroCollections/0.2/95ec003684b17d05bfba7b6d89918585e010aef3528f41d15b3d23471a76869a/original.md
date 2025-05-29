```
EmptyVector() :: AbstractVector{Union{}}
EmptyVector(itr) :: AbstractVector
EmptyVector{T}() :: AbstractVector{T}
EmptyVector{T}(itr) :: AbstractVector{T}
```

Create an empty vector.  Iterator `itr` must be empty.

The unary constructors `EmptyVector(itr)` and `EmptyVector{T}(itr)` asserts that the iterator `itr` is empty.  The constructor `EmptyVector(itr)` uses `eltype(itr)` if `IteratorEltype(itr)` is `HasEltype`.
