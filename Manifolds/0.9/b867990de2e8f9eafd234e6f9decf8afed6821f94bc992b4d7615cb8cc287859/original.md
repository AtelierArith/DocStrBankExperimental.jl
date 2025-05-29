```
project(M::HeisenbergGroup, p, X)
```

Project a matrix `X` in the Euclidean embedding onto the Lie algebra of [`HeisenbergGroup`](@ref) `M`. Sets the diagonal elements to 0 and all non-diagonal elements except the first row and the last column to 0.
