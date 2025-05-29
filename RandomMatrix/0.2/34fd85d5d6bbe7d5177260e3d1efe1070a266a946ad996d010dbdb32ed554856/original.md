```julia
GOE <: ContinuousMatrixDistribution
GOE(n) 
```

  * `n` : dimension
  * The **Gaussian Orthogonal Ensemble** (`GOE`) is an ensemble of random $n \times n$ Symmetric matrices    $M_{n}$ in which the upper-triangular entries are iid with distribution $N(0,1)_{\mathbf{R}}$,    and the diagonal entries are iid with distribution $N(0,2)_{\mathbf{R}}$, and independent of the upper-triangular ones

```julia
rand(M::GOE, norm::bool)
```

  * `norm` : default `false`,  if `norm` set to `true`, then the matrix will be normlaized with $\operatorname{min}(n,m)^{-1/2}$.

# Examples

Generate a 3 by 3 random matrix from GOE(3)

```julia
rand(GOE(3))

3×3 Symmetric{Float64, Matrix{Float64}}:
 -1.62391   -0.451433    0.863883
 -0.451433   0.0271799  -0.524854
  0.863883  -0.524854   -0.00930624
```

```julia
rand(GOE(3),norm=true)

3×3 Symmetric{Float64, Matrix{Float64}}:
  0.302141   0.152634   -0.711679
  0.152634  -0.0629327   0.103075
 -0.711679   0.103075    1.51861
```
