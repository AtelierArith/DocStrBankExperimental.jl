```
Strang([T=Int,] n::Int)
```

Construct `Strang` matrix with elements of type `T`. This special matrix named after Gilbert Strang is symmetric, tridiagonal, and Toeplitz. See Fig. 1 of [Julia paper](https://doi.org/10.1137/141000671).

```jldoctest
julia> Strang(4)
4×4 Strang{Int64}:
  2  -1   0   0
 -1   2  -1   0
  0  -1   2  -1
  0   0  -1   2

julia> Strang(Int16, 3)
3×3 Strang{Int16}:
  2  -1   0
 -1   2  -1
  0  -1   2
```
