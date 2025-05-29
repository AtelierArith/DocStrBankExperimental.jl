```julia
ForwardDiffSensitivity{CS, CTS} <: AbstractForwardSensitivityAlgorithm{CS, Nothing, Nothing}
```

An implementation of discrete forward sensitivity analysis through ForwardDiff.jl. When used within adjoint differentiation (i.e. via Zygote), this will cause forward differentiation of the `solve` call within the reverse-mode automatic differentiation environment.

## Constructor

```julia
ForwardDiffSensitivity(; chunk_size = 0, convert_tspan = nothing)
```

## Keyword Arguments

  * `chunk_size`: the chunk size used by ForwardDiff for computing the Jacobian, i.e. the number of simultaneous columns computed.
  * `convert_tspan`: whether to convert time to also be `Dual` valued. By default this is `nothing` which will only convert if callbacks are found. Conversion is required in order to accurately differentiate callbacks (hybrid equations).

## SciMLProblem Support

This `sensealg` supports any `SciMLProblem`s, provided that the solver algorithms is `SciMLBase.isautodifferentiable`. Note that `ForwardDiffSensitivity` can accurately differentiate code with callbacks only when `convert_tspan=true`.
