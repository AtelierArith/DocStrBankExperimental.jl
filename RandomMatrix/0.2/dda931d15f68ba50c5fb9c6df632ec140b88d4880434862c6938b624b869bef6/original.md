```julia
randSymmetric(d, n; Diag, norm) 

randSymmetric(n; norm)
```

  * `d` : entry distribution
  * `n` : dimensions
  * `norm` : default  `false`, if `norm` set to `true`, then the matrix will be normalized with $n^{-1/2}$.
  * `diag` : default `diag = d`, the distribution for diagonal entries.    To use a different distribution (say Binomial) for digonal elements, set `diag = Binomial(1,0.5)`
  * See also [`GOE`](@ref)

# Examples

Generates a 3 by 3 random Symmetric matrix with entries from the Standard Gaussian.

```julia
randSymmetric(3)

3×3 Symmetric{Float64, Matrix{Float64}}:
 -0.230698  -1.72846     0.306362
 -1.72846    0.0845915  -0.0116108
  0.306362  -0.0116108  -0.559046
```
