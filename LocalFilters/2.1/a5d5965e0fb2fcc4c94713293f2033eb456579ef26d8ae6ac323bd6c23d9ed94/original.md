```
localfilter([T=eltype(A),] A, B, initial, update, final=identity; kwds...) -> dst
```

out of place version of [`localfilter!`](@ref) which is equivalent to:

```
localfilter!(similar(A, T), A, B, initial, update, final=identity; kwds...)
```

Optional argument `T` is to specify the element type of the result; by default, `T` is the element type of `A`.
