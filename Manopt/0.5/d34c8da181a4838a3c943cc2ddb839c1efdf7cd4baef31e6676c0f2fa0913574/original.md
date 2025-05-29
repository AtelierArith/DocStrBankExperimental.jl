```
TruncatedConjugateGradientState <: AbstractHessianSolverState
```

describe the Steihaug-Toint truncated conjugate-gradient method, with

# Fields

Let `T` denote the type of a tangent vector and `R <: Real`.

  * `δ::T`:                     the conjugate gradient search direction
  * `δHδ`, `YPδ`, `δPδ`, `YPδ`: temporary inner products with `Hδ` and preconditioned inner products.
  * `Hδ`, `HY`:                 temporary results of the Hessian applied to `δ` and `Y`, respectively.
  * `κ::R`:                     the linear convergence target rate.
  * `project!`:                 for numerical stability it is possible to project onto the tangent space after every iteration. the function has to work inplace of `Y`, that is `(M, Y, p, X) -> Y`, where `X` and `Y` can be the same memory.
  * `randomize`:          indicate whether `X` is initialised to a random vector or not
  * `residual::T`:                 the gradient of the model $m(Y)$
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `θ::R`:                     the superlinear convergence target rate of $1+θ$
  * `trust_region_radius::R`:   the trust-region radius
  * `X::T`:                     the gradient $\operatorname{grad}f(p)$
  * `Y::T`:                     current iterate tangent vector
  * `z::T`:                     the preconditioned residual
  * `z_r::R`:                   inner product of the residual and `z`

# Constructor

```
TruncatedConjugateGradientState(TpM::TangentSpace, Y=rand(TpM); kwargs...)
```

Initialise the TCG state.

## Input

  * `TpM`: a [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`)

## Keyword arguments

  * `κ=0.1`
  * `project!::F=copyto!`: initialise the numerical stabilisation to just copy the result
  * `randomize=false`
  * `θ=1.0`
  * `trust_region_radius=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(base_manifold(TpM)) / 4`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(base_manifold(Tpm))``)`[`|`](@ref StopWhenAny)[`StopWhenResidualIsReducedByFactorOrPower`](@ref)`(; κ=κ, θ=θ)`[`|`](@ref StopWhenAny)[`StopWhenTrustRegionIsExceeded`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenCurvatureIsNegative`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenModelIncreased`](@ref)`()`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$

# See also

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
