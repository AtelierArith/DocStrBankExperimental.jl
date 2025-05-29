```
∇A, ∇B, ∇C, ∇D, hn, ω = hinfgrad(sys; rtolinf=1e-8, kwargs...)
∇A, ∇B, ∇C, ∇D        = hinfgrad(sys, hn, ω)
```

Compute the gradient of the H∞ norm w.r.t. the statespace matrices `A,B,C,D`. If only a system is provided, the norm `hn` and the peak frequency `ω` are automatically calculated. `kwargs` are sent to [`hinfnorm2`](@ref). Note, the default tolerance to which the norm is calculated is set smaller than default for [`hinfnorm2`](@ref), gradients will be discontinuous with any non-finite tolerance, and sensitive optimization algorithms may require even tighter tolerance.

In cases where the maximum singular value is reached at more than one frequency, a random frequency is used.

If the system is unstable, the gradients are `NaN`. Strategies to find an initial stabilizing controllers are outlined in Apkarian and D. Noll, "Nonsmooth H∞ Synthesis" in IEEE Transactions on Automatic Control.

An `rrule` for ChainRules is defined using this function, so `hn` is differentiable with any AD package that derives its rules from ChainRules (only applies to the `hn` return value, not `ω`).
