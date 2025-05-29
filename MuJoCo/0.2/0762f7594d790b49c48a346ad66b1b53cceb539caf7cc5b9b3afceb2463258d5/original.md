```
mju_cholUpdate(mat, x, flg_plus)
```

Cholesky rank-one update: L*L' +/- x*x'; return rank.

# Arguments

  * **`mat::Matrix{Float64}`** -> A matrix of variable size. `mat` should be a square matrix.
  * **`x::Vector{Float64}`** -> A vector of variable size. `x` should be a vector, not a matrix.
  * **`flg_plus::Int32`**
