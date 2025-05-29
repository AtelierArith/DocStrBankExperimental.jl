```julia
randTriangular(d , n ;  diag , Diag, upper ) 

randTriangular(n;diag, upper)
```

  * `d` : entry distribution
  * `n` : dimension
  * `diag` : default `diag = d`, diagonal entry distribution
  * `Diag` : default `Diag = true`, `true` includes diagonal, `false` with diagonal entries 0
  * `upper` : default `upper = true`, `true` gives upper triangular, `false` gives lower triangular

# Examples

Generate an upper triangular matrix with entries Standard Normal

```julia
randTriangular(3)

3×3 UpperTriangular{Float64, Matrix{Float64}}:
 -0.572757  -0.459518   -1.60622
   ⋅         0.0216834  -0.416529
   ⋅          ⋅         -1.00807
```

Generate a 3 by 3 strictly lower triangular matrix, with nonzero entries uniform from $\{1,2,3\}$ 

```julia
randTriangular(1:3,3,upper=false,Diag=false)

3×3 LowerTriangular{Int64, Transpose{Int64, Matrix{Int64}}}: 
 0  ⋅  ⋅
 3  0  ⋅
 3  2  0
```
