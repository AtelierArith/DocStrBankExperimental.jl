```
SingletonVector(itr) :: AbstractVector
SingletonVector{T}(itr) :: AbstractVector{T}
```

Create a singleton vector.  Iterator `itr` must have one and only one element.

The constructor `SingletonVector(itr)` uses `eltype(itr)` if `IteratorEltype(itr)` is `HasEltype`.
