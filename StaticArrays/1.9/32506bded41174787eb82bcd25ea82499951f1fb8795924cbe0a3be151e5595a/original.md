```
@MArray [a b; c d]
@MArray [[a, b];[c, d]]
@MArray [i+j for i in 1:2, j in 1:2]
@MArray ones(2, 2, 2)
```

A convenience macro to construct `MArray` with arbitrary dimension. See [`@SArray`](@ref) for detailed features.
