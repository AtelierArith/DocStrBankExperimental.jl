```
exp_and_gram!(
    eA::AbstractMatrix{T},
    G::AbstractMatrix{T},
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AbstractExpAndGramAlgorithm,
    cache = alloc_mem(A, B, method),
)
```

行列 A * t の行列指数と、区間 [0, t] における (A, B) の制御可能性グラミアンを計算します。t が省略された場合は、単位区間が使用されます。結果は (eA, G) に格納され、返されます。
