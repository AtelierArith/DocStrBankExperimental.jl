```
exp_and_gram_chol(
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AbstractExpAndGramAlgorithm,
)
```

行列 A * t の行列指数と、(A, B) の制御可能性グラミアンを区間 [0, t] で計算します。t が省略された場合は、単位区間が使用されます。
