```
predict(M::HeteroPCAModel, X::AbstractMatrix; λ = 0.0)
```

列ごとのバージョン：`k × n` 行列を返し、その *j* 番目の列は `predict(M, X[:, j]; λ = λ)` です。
