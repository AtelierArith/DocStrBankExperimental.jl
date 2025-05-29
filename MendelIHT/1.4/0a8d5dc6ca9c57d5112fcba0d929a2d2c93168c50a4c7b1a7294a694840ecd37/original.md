```
random_covariance_matrix(n::Int, [κ=10])
```

Generates a `n × n` positive definite, symmetric matrix with condition number less than `κ` https://discourse.julialang.org/t/generate-a-positive-definite-matrix/48582

Both issymmetric(random*covariance*matrix(n)) and isposdef(random*covariance*matrix(n)) will always return true, and cond(random*covariance*matrix(n)) ≤ κ
