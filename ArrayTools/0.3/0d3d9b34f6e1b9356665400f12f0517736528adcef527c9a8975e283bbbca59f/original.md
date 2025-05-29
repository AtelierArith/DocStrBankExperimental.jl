```
colons(n)
```

yields a `n`-tuple of colons `:` (a.k.a. `Colon()`).

When `n` is known at compile time, it is faster to call:

```
colons(Val(n))
```

This method is suitable to extract sub-arrays of build views when some kind of rubber index is needed. For instance:

```
slice(A::AbstractArray{T,N}, i::Integer) where {T,N} =
    A[colons(Val(N-1))..., i]
```

defines a function that returns the `i`-th slice of `A` assuming index `i` refers the last index of `A`. Using the rubber-index `..`, a shorter definition is:

```
slice(A::AbstractArray, i) = A[.., i]
```

which is also able to deal with multiple trailing indices if `i` is a `CartesianIndex`.

See also: `..`, [`RubberIndex`](@ref).
