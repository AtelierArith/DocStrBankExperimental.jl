```
exp_and_gram_chol!(
    eA::AbstractMatrix{T},
    U::AbstractMatrix{T},
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::ExpAndGram{T,q},
    [cache = alloc_mem(A, B, method)],
)

exp_and_gram_chol!(
    eA::AbstractMatrix{T},
    U::AbstractMatrix{T},
    A::AbstractMatrix{T},
    B::AbstractVecOrMat{T},
    [t::Number],
    method::AdaptiveExpAndGram,
    [cache = nothing],
)

行列 A * t の行列指数と、区間 [0, t] における (A, B) の制御可能性グラミアンを計算します。t が省略された場合は単位区間が使用されます。結果は (eA, U) に格納され、返されます。
```
