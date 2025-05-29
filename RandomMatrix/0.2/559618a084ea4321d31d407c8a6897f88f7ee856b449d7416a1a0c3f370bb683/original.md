```julia
randToeplitz(d, n;  norm, hermitian)  
```

  * `d` : entry distribution
  * `n` : dimension
  * `norm` : default `false`;  if `norm` set to `true`, then the matrix will be normlaized with $n^{-1/2}$.
  * `hermitian`: default `true`; if `true` the matrix will be Hermitian

# Examples

Generate a $4 \times 4$ random Hermitian Toeplitz matrix with entries Standard Normal.

```julia
randToeplitz(4)

4×4 Matrix{Float64}:
  1.10207   -0.47292   -0.745498   1.06809
 -0.47292    1.10207   -0.47292   -0.745498
 -0.745498  -0.47292    1.10207   -0.47292
  1.06809   -0.745498  -0.47292    1.10207
```

Generate a $4 \times 4$ normalized random Toeplitz matrix with entries `Exponential(1)`.

```julia
using Distributions
randToeplitz(Exponential(1),4, norm = true, hermitian = false)

4×4 Matrix{Float64}:
 0.667888  0.260045  1.48812   0.477305
 1.50374   0.667888  0.260045  1.48812
 1.1475    1.50374   0.667888  0.260045
 0.363966  1.1475    1.50374   0.667888
```
