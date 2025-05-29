```julia
randOrthogonal(n::Int)
```

  * Generates a `n` by `n` random Orthogonal matrix
  * Equivalent to `rand(Haar(1,n))`, see [`Haar`](@ref) and [`COE`](@ref)
  * For unitary matrices, use `randUnitary` or `rand(Haar(2,n))` instead
  * The algorithm is disccused in [How to Generate Random Matrices from the Classical Compact Groups](http://www.ams.org/notices/200705/fea-mezzadri-web.pdf)

# Examples

Generates a 3 by 3 random Orthogonal matrix 

```julia
randOrthogonal(3)

3×3 Matrix{Float64}:
 -0.875553  0.112448   0.469853
 -0.147915  0.863441  -0.482277
  0.459921  0.491757   0.739356
```
