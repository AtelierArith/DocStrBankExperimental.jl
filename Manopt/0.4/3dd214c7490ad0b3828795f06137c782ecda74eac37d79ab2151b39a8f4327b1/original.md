```
TruncatedConjugateGradientState <: AbstractHessianSolverState
```

describe the Steihaug-Toint truncated conjugate-gradient method, with

# Fields

a default value is given in brackets if a parameter can be left out in initialization.

  * `Y`:                   (`zero_vector(M,p)`) Current iterate, whose type is also used for the other, internal, tangent vector fields
  * `stop`:                a [`StoppingCriterion`](@ref).
  * `X`:                   the gradient $\operatorname{grad}f(p)$`
  * `δ`:                   the conjugate gradient search direction
  * `θ`:                   (`1.0`) 1+θ is the superlinear convergence target rate.
  * `κ`:                   (`0.1`) the linear convergence target rate.
  * `trust_region_radius`: (`injectivity_radius(M)/4`) the trust-region radius
  * `residual`:            the gradient of the model $m(Y)$
  * `randomize`:           (`false`)
  * `project!`:            (`copyto!`) for numerical stability it is possible to project onto the tangent space after every iteration. By default this only copies instead.

# Internal fields

  * `Hδ`, `HY`:                 temporary results of the Hessian applied to `δ` and `Y`, respectively.
  * `δHδ`, `YPδ`, `δPδ`, `YPδ`: temporary inner products with `Hδ` and preconditioned inner products.
  * `z`:                        the preconditioned residual
  * `z_r`:                      inner product of the residual and `z`

# Constructor

```
TruncatedConjugateGradientState(TpM::TangentSpace, Y=rand(TpM); kwargs...)
```

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
