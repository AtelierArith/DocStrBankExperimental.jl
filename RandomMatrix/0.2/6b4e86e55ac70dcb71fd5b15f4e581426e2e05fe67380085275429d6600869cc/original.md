```julia
randUnitary(n::Int)
```

  * Generates a n by n random Unitary matrix
  * Equivalent to  `rand(Haar(2,n))`, see [`Haar`](@ref) and [`CUE`](@ref)
  * For orthogonal matrices, use `randOrthogonal` or `rand(Haar(1,n))` instead
  * The algorithm is disccused in [How to Generate Random Matrices from the Classical Compact Groups](http://www.ams.org/notices/200705/fea-mezzadri-web.pdf)

# Examples

Generate a 3 by 3 random Unitary matrix 

```julia
randUnitary(3)

3×3 Matrix{ComplexF64}:
 -0.149398+0.0572715im  -0.0935861+0.629201im  -0.257255-0.709625im
  0.337035-0.342606im     -0.36366+0.599236im  -0.100838+0.517231im
  -0.17097+0.845103im   -0.0767105+0.313259im   0.247081+0.3025im
```
