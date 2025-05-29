```
@SMatrix [a b c d]
@SMatrix [[a, b];[c, d]]
@SMatrix [i+j for i in 1:2, j in 1:2]
@SMatrix ones(2, 2)
```

A convenience macro to construct `SMatrix`. See [`@SArray`](@ref) for detailed features.
