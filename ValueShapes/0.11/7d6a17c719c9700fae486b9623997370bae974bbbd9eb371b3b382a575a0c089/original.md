```
realnumtype(T::Type)
```

Return the underlying numerical type of T that's a subtype of `Real`.

Uses type promotion among underlying `Real` type in `T`.

e.g.

```julia

A = fill(fill(rand(Float32, 5), 10), 5)
realnumtype(typeof(A)) == Float32
```
