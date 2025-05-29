```
SemFiniteDiff(;observed = SemObservedData, implied = RAM, loss = SemML, kwargs...)
```

A wrapper around [`Sem`](@ref) that substitutes dedicated evaluation of gradient and hessian with finite difference approximation.

# Arguments

  * `observed`: object of subtype `SemObserved` or a constructor.
  * `implied`: object of subtype `SemImplied` or a constructor.
  * `loss`: object of subtype `SemLossFunction`s or constructor; or a tuple of such.

Returns a Sem with fields

  * `observed::SemObserved`: Stores observed data, sample statistics, etc. See also [`SemObserved`](@ref).
  * `implied::SemImplied`: Computes model implied statistics, like Σ, μ, etc. See also [`SemImplied`](@ref).
  * `loss::SemLoss`: Computes the objective and gradient of a sum of loss functions. See also [`SemLoss`](@ref).
