```
counterfactual(model::AbstractSDM, x::Vector{T}, yhat, λ; maxiter=100, minvar=5e-5, kwargs...) where {T <: Number}
```

入力ベクトル `x` と目標ルール `yhat` に基づいて1つの反実仮想説明を生成します。学習率は `λ` です。Nelder-Meadアルゴリズムで使用される最大反復回数は `maxiter` であり、モデルが停止するための分散改善は `minvar` です。他のキーワードは `predict` に渡されます。
