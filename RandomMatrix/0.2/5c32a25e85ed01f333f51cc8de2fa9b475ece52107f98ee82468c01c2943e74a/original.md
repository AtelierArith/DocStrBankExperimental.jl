```julia
randHermitian(d, n; diag, norm )

randHermitian(n; norm)
```

  * `d` : entry distribution
  * `n`  : dimensions
  * `norm` : default `false`, if `norm` set to `true`, then the matrix will be normalized with $n^{-1/2}$.
  * `diag` : default `diag = d`, diagonal entry distribution.    To use a different distribution (say Circular(2)) for digonal elements, set `diag = Circular(2)`.     The diagonal entries will always be forced to have imgainary part `0`.
  * See also [`GUE`](@ref)

# Examples

Generates a 2 by 2 random Hermitian matrix with off-diagonal entries from the Standard Complex Gaussian, and Standard Normal on the diagonal.

```julia
randHermitian(2)

2×2 Hermitian{ComplexF64, Matrix{ComplexF64}}:
  0.382095+0.0im        -0.708469-0.0636734im
 -0.708469+0.0636734im   0.336952+0.0im
```

Generate a 3 by 3 Hermitian matrix, with off-diagonal entries [`Circular`](@ref)(1) and diagonal entries uniformly `-1` or `1`.

```julia
randHermitian(Circular(1),3,diag = (-1,1))

3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
     1.0+0.0im       1.56259-0.676099im  1.39468-0.295073im
 1.56259+0.676099im     -1.0+0.0im       1.53369+0.296583im
 1.39468+0.295073im  1.53369-0.296583im     -1.0+0.0im
```

Generate a random 2 by 2 Symmetric Matrix with entries  `Poisson(2)` rvs.  This is also be done with `randSymmetric(Poisson(2),3)`

```julia
randHermitian(Poisson(2),3)

3×3 Hermitian{Int64, Matrix{Int64}}:
 3  1  0
 1  1  2
 0  2  1
```

Entries uniformly from $\{1,2,3,...,10\}$

```julia
randHermitian(1:10,2)

2×2 Hermitian{Int64, Matrix{Int64}}:
 10  7
  7  6
```

Entries either -1 or pi with equal probability

```julia
randHermitian([-1,pi],3)

3×3 Hermitian{Float64, Matrix{Float64}}:
  3.14159  -1.0      -1.0
 -1.0      -1.0       3.14159
 -1.0       3.14159   3.14159
```
