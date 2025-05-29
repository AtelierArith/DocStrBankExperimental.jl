```
@MMatrix [a b c d]
@MMatrix [[a, b];[c, d]]
@MMatrix [i+j for i in 1:2, j in 1:2]
@MMatrix ones(2, 2)
```

A convenience macro to construct `MMatrix`. See [`@SArray`](@ref) for detailed features.
