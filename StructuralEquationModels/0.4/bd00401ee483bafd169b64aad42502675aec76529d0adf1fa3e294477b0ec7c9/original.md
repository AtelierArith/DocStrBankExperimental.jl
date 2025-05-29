```
Sem(;observed = SemObservedData, implied = RAM, loss = SemML, kwargs...)
```

Constructor for the basic `Sem` type. All additional kwargs are passed down to the constructors for the observed, implied, and loss fields.

# Arguments

  * `observed`: object of subtype `SemObserved` or a constructor.
  * `implied`: object of subtype `SemImplied` or a constructor.
  * `loss`: object of subtype `SemLossFunction`s or constructor; or a tuple of such.

Returns a Sem with fields

  * `observed::SemObserved`: Stores observed data, sample statistics, etc. See also [`SemObserved`](@ref).
  * `implied::SemImplied`: Computes model implied statistics, like Σ, μ, etc. See also [`SemImplied`](@ref).
  * `loss::SemLoss`: Computes the objective and gradient of a sum of loss functions. See also [`SemLoss`](@ref).
