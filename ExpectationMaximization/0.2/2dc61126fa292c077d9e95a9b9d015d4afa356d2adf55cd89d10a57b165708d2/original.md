```
fit_mle(mix::AbstractArray{<:MixtureModel}, y::AbstractVecOrMat, weights...; method = ClassicEM(), display=:none, maxiter=1000, atol=1e-3, rtol=nothing, robust=false, infos=false)
```

Do the same as `fit_mle` for each (initial) mixtures in the mix array. Then it selects the one with the largest loglikelihood. Warning: It uses try and catch to avoid errors messages in case EM converges toward a singular solution (probably using robust should be enough in most case to avoid errors).
