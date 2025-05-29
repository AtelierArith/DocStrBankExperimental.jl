```
counterfactual(model::AbstractSDM, x::Vector{T}, yhat, λ; maxiter=100, minvar=5e-5, kwargs...) where {T <: Number}
```

Generates one counterfactual explanation given an input vector `x`, and a target rule to reach `yhat`. The learning rate is `λ`. The maximum number of iterations used in the Nelder-Mead algorithm is `maxiter`, and the variance improvement under which the model will stop is `minvar`. Other keywords are passed to `predict`.
