```julia
randDiagonal(d, n) 

randDiagonal(n) 
```

  * `d` : default `Normal(0，1)`, entry distribution
  * `n` : dimension

# Examples

Generates a 3 by 3 diagonal matrix, with non-zero elements from `Normal(0,1)`

```julia
randDiagonal(3)

3×3 Diagonal{Float64, Vector{Float64}}:
 0.440359   ⋅         ⋅
  ⋅        1.94832    ⋅
  ⋅         ⋅       -0.52536
```

Generates a 5 by 5 diagonal matrix, with non-zero elements from `Poisson(2)`

```julia
randDiagonal(Poisson(2),5)

5×5 Diagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  0  ⋅  ⋅  ⋅
 ⋅  ⋅  0  ⋅  ⋅
 ⋅  ⋅  ⋅  3  ⋅
 ⋅  ⋅  ⋅  ⋅  3
```
