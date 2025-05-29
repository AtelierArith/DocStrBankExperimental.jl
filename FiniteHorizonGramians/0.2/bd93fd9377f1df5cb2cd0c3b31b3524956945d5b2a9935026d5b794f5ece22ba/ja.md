```
exp_and_gram(
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AbstractExpAndGramAlgorithm,
)
```

行列指数 exp(A) と (A, B) の制御可能性グラミアンを区間 [0, t] で計算します。t が省略された場合は単位区間が使用されます。
