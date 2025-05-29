```
Score(DM::DataModel, θ::AbstractVector{<:Number}; ADmode::Val=Val(:ForwardDiff))
```

Calculates the gradient of the log-likelihood $\ell$ with respect to a set of parameters $\theta$. `ADmode=Val(false)` computes the Score using the Jacobian `dmodel` provided in `DM`, i.e. by having to separately evaluate both the `model` as well as `dmodel`. Other choices of `ADmode` directly compute the Score by differentiating the formula the log-likelihood, i.e. only one evaluation on a dual variable is performed.
