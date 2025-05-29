```julia
ForwardDiffOverAdjoint{A} <: AbstractSecondOrderSensitivityAlgorithm{nothing, true, nothing}
```

ForwardDiff.jl over a choice of `sensealg` method for the adjoint.

## Constructor

```julia
ForwardDiffOverAdjoint(sensealg)
```

## SciMLProblem Support

This supports any SciMLProblem that the `sensealg` choice supports, provided the solver algorithm is `SciMLBase.isautodifferentiable`.

## References

Hindmarsh, A. C. and Brown, P. N. and Grant, K. E. and Lee, S. L. and Serban, R. and Shumaker, D. E. and Woodward, C. S., SUNDIALS: Suite of nonlinear and differential/algebraic equation solvers, ACM Transactions on Mathematical Software (TOMS), 31, pp:363–396 (2005)
