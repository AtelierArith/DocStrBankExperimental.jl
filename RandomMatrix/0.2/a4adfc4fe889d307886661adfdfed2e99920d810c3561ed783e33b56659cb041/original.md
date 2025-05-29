```julia
GUE <: ContinuousMatrixDistribution
GUE(n)
```

  * `n` : dimension
  * The **Gaussian Unitary Ensemble** (`GUE`) is an ensemble of random $n \times n$ Hermitian matrices    $M_{n}$ in which the upper-triangular entries are iid with distribution $N(0,1)_{\mathbf{C}}$,    and the diagonal entries are iid with distribution $N(0,1)_{\mathbf{R}}$, and independent of the upper-triangular ones

```julia
rand(M::GUE, norm::bool) 
```

  * `norm` : default `false`,  if `norm` set to `true`, then the matrix will be normlaized with $\operatorname{min}(n,m)^{-1/2}$.

# Examples

Generate a 3 by 3 random matrix from GUE(3)

```julia
rand(GUE(3))

3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 -0.883413+0.0im         1.09872+0.874884im     -0.1985-1.04778im
   1.09872-0.874884im    1.55483+0.0im        -0.488532+1.18694im
   -0.1985+1.04778im   -0.488532-1.18694im   -0.0823873+0.0im
```

```julia
rand(GUE(2),norm=true)
2×2 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 -0.457089+0.0im       -0.672713-0.102234im
 -0.672713+0.102234im   0.380126+0.0im
```
