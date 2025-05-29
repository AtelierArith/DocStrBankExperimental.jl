```
LikelihoodProblem{N,P,D,L,Θ,S} <: AbstractLikelihoodProblem
```

Struct representing a likelihood problem. 

# Fields

  * `problem::P`

The associated `OptimizationProblem`.

  * `data::D`

The argument `p` used in the log-likelihood function. 

  * `log_likelihood_function::L`

The log-likelihood function, taking the form `ℓ(θ, p)`.

  * `θ₀::Θ`

Initial estimates for the MLE `θ`.

  * `syms::S`

Variable names for the parameters. This is wrapped into a `SymbolCache` from SymbolicIndexingInterface.jl.

The extra parameter `N` is the number of parameters.

# Constructors

## Standard

```
LikelihoodProblem(loglik::Function, θ₀;
    syms=eachindex(θ₀), data=SciMLBase.NullParameters(),
    f_kwargs=nothing, prob_kwargs=nothing)
```

Constructor for the [`LikelihoodProblem`](@ref).

### Arguments

  * `loglik::Function`: The log-likelihood function, taking the form `ℓ(θ, p)`.
  * `θ₀`: The estimates estimates for the MLEs.

### Keyword Arguments

  * `syms=eachindex(θ₀)`: Names for each parameter.
  * `data=SciMLBase.NullParameters()`: The parameter `p` in the log-likelihood function.
  * `f_kwargs=nothing`: Keyword arguments, passed as a `NamedTuple`, for the `OptimizationFunction`.
  * `prob_kwargs=nothing`: Keyword arguments, passed as a `NamedTuple`, for the `OptimizationProblem`.

### Outputs

Returns the [`LikelihoodProblem`](@ref) problem object.

## With arguments for a differential equation problem

```
LikelihoodProblem(loglik::Function, θ₀,
    ode_function, u₀, tspan;
    syms=eachindex(θ₀), data=SciMLBase.NullParameters(),
    ode_parameters=SciMLBase.NullParameters(), ode_alg,
    ode_kwargs=nothing, f_kwargs=nothing, prob_kwargs=nothing)
```

Constructor for the [`LikelihoodProblem`](@ref) for a differential equation problem.

### Arguments

  * `loglik::Function`: The log-likelihood function, taking the form `ℓ(θ, p, integrator)`.
  * `θ₀`: The estimates estimates for the MLEs.
  * `ode_function`: The function `f(du, u, p, t)` or `f(u, p, t)` for the differential equation.
  * `u₀`: The initial condition for the differential equation.
  * `tspan`: The time-span to solve the differential equation over.

### Keyword Arguments

  * `syms=eachindex(θ₀)`: Names for each parameter.
  * `data=SciMLBase.NullParameters()`: The parameter `p` in the log-likelihood function.
  * `ode_parameters=SciMLBase.NullParameters()`: The parameter `p` in `ode_function`.
  * `ode_alg`: The algorithm used for solving the differential equatios.
  * `ode_kwargs=nothing`: Extra keyword arguments, passed as a `NamedTuple`, to pass into the integrator; see `construct_integrator`.
  * `f_kwargs=nothing`: Keyword arguments, passed as a `NamedTuple`, for the `OptimizationFunction`.
  * `prob_kwargs=nothing`: Keyword arguments, passed as a `NamedTuple`, for the `OptimizationProblem`.

### Outputs

Returns the [`LikelihoodProblem`](@ref) problem object.

## With an integrator

```
LikelihoodProblem(loglik::Function, θ₀, integrator;
    syms=eachindex(θ₀), data=SciMLBase.NullParameters(),
    f_kwargs=nothing, prob_kwargs=nothing)
```

Constructor for the [`LikelihoodProblem`](@ref) for a differential equation problem  with associated `integrator`.

### Arguments

  * `loglik::Function`: The log-likelihood function, taking the form `ℓ(θ, p, integrator)`.
  * `θ₀`: The estimates estimates for the MLEs.
  * `integrator`: The integrator for the differential equation problem. See also `construct_integrator`.

### Keyword Arguments

  * `syms=eachindex(θ₀)`: Names for each parameter.
  * `data=SciMLBase.NullParameters()`: The parameter `p` in the log-likelihood function.
  * `f_kwargs=nothing`: Keyword arguments, passed as a `NamedTuple`, for the `OptimizationFunction`.
  * `prob_kwargs=nothing`: Keyword arguments, passed as a `NamedTuple`, for the `OptimizationProblem`.

### Outputs

Returns the [`LikelihoodProblem`](@ref) problem object.
