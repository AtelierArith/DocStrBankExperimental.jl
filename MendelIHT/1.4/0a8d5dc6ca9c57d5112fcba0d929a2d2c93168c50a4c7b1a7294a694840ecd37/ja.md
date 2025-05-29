```
random_covariance_matrix(n::Int, [κ=10])
```

`n × n` の正定値対称行列を生成し、条件数は `κ` 未満です https://discourse.julialang.org/t/generate-a-positive-definite-matrix/48582

issymmetric(random*covariance*matrix(n)) と isposdef(random*covariance*matrix(n)) は常に true を返し、cond(random*covariance*matrix(n)) ≤ κ です。
