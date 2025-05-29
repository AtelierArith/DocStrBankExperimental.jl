```
project(M::HeisenbergGroup, p)
```

Project a matrix `p` in the Euclidean embedding onto the [`HeisenbergGroup`](@ref) `M`. Sets the diagonal elements to 1 and all non-diagonal elements except the first row and the last column to 0.
