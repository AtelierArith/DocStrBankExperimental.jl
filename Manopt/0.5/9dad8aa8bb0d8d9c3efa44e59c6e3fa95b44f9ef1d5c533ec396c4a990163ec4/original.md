```
ConjugateGradientState <: AbstractGradientSolverState
```

specify options for a conjugate gradient descent algorithm, that solves a [`DefaultManoptProblem`].

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `δ`:                       the current descent direction, also a tangent vector
  * `β`:                       the current update coefficient rule, see .
  * `coefficient`:             function to determine the new `β`
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# Constructor

```
ConjugateGradientState(M::AbstractManifold; kwargs...)
```

where the last five fields can be set by their names as keyword and the `X` can be set to a tangent vector type using the keyword `initial_gradient` which defaults to `zero_vector(M,p)`, and `δ` is initialized to a copy of this vector.

## Keyword arguments

The following fields from above <re keyword arguments

  * `initial_gradient=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `coefficient=[`ConjugateDescentCoefficient`](@ref)`()`: specify a CG coefficient, see also the [`ManifoldDefaultsFactory`](@ref).
  * `stepsize=`[`default_stepsize`](@ref)`(M, ConjugateGradientDescentState; retraction_method=retraction_method)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`): a functor indicating that the stopping criterion is fulfilled
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# See also

[`conjugate_gradient_descent`](@ref), [`DefaultManoptProblem`](@ref), [`ArmijoLinesearch`](@ref)
