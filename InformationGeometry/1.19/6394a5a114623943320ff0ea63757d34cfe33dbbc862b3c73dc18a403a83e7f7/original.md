```
OrthVF(DM::DataModel, PL::Plane, θ::AbstractVector{<:Number}; ADmode::Val=Val(:ForwardDiff)) -> Vector
```

Calculates a direction (in parameter space) in which the value of the log-likelihood does not change, given a parameter configuration $\theta$. Since a 2D `Plane` is specified, both the input `θ` as well as well as the output have 2 components. `ADmode=Val(false)` computes the Score by separately evaluating the `model` as well as the Jacobian `dmodel` provided in `DM`. Other choices of `ADmode` directly compute the Score by differentiating the formula the log-likelihood, i.e. only one evaluation on a dual variable is performed.
