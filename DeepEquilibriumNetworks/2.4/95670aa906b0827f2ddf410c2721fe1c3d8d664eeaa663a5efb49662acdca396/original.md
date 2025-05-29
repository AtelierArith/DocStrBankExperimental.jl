```
DeepEquilibriumNetwork(model, solver; init = missing, jacobian_regularization=nothing,
    problem_type::Type=SteadyStateProblem{false}, kwargs...)
```

Deep Equilibrium Network as proposed in [baideep2019](@cite) and [pal2022mixing](@cite).

## Arguments

  * `model`: Neural Network.
  * `solver`: Solver for the rootfinding problem. ODE Solvers and Nonlinear Solvers are both supported.

## Keyword Arguments

  * `init`: Initial Condition for the rootfinding problem. If `nothing`, the initial condition is set to `zero(x)`. If `missing`, the initial condition is set to `WrappedFunction(zero)`. In other cases the initial condition is set to `init(x, ps, st)`.
  * `jacobian_regularization`: Must be one of `nothing`, `AutoForwardDiff`, `AutoFiniteDiff` or `AutoZygote`.
  * `problem_type`: Provides a way to simulate a Vanilla Neural ODE by setting the `problem_type` to `ODEProblem`. By default, the problem type is set to `SteadyStateProblem`.
  * `kwargs`: Additional Parameters that are directly passed to `SciMLBase.solve`.

## Example

```jldoctest
julia> model = DeepEquilibriumNetwork(
           Parallel(+, Dense(2, 2; use_bias=false), Dense(2, 2; use_bias=false)),
           VCABM3(); verbose=false);

julia> rng = Xoshiro(0);

julia> ps, st = Lux.setup(rng, model);

julia> size(first(model(ones(Float32, 2, 1), ps, st)))
(2, 1)
```

See also: [`SkipDeepEquilibriumNetwork`](@ref), [`MultiScaleDeepEquilibriumNetwork`](@ref), [`MultiScaleSkipDeepEquilibriumNetwork`](@ref).
