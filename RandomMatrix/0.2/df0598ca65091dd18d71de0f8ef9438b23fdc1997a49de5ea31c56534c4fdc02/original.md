```julia
randMatrix(d::D, n::Int, m = n::Int; norm = false::Bool) where D<:S

randMatrix(n::Int, m = n::Int; norm = false::Bool)
```

  * `d` : entry distribution
  * `n`,`m` : default `m = n` , dimensions
  * `norm` : default `false`, if `norm` set to `true`, then the matrix will be normlaized with $\operatorname{min}(n,m)^{-1/2}$.

# Examples

Generates a 2 by 2 random  matrix with entries from the Standard  Gaussian.

```julia
randMatrix(2)

2×2 Matrix{Float64}:
 1.74043  -1.30317
 0.72765   0.639943
```

Generates a 3 by 2 random  matrix with entries uniformly from {1,2,3,...,10}.

```julia
randMatrix(1:10,3,2)

3×2 Matrix{Int64}:
  1  3
  6  4
 10  1
```

Generate a normalized random 2 by 2  Matrix with entries  `Poisson(2)` rvs.  Need to import the `Distributions` package for `Poisson(2)`

```julia
using Distributions
randMatrix(Poisson(2),2,norm = true)

2×2 Matrix{Float64}:
 1.41421   0.0
 0.707107  1.41421
```
