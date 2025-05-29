```
BossProblem(; kwargs...)
```

Defines the whole optimization problem for the BOSS algorithm.

# Problem Definition

```
There is some (noisy) blackbox function `y = f(x) = f_true(x) + ϵ` where `ϵ ~ Normal`.

We have some surrogate model `y = model(x) ≈ f_true(x)`
describing our knowledge (or lack of it) about the blackbox function.

We wish to find `x ∈ domain` such that `fitness(f(x))` is maximized
while satisfying the constraints `f(x) <= y_max`.
```

# Keywords

  * `fitness::Fitness`: The [`Fitness`](@ref) function.
  * `f::Union{Function, Missing}`: The objective blackbox function.
  * `model::SurrogateModel`: The [`SurrogateModel`](@ref).
  * `data::ExperimentData`: The initial data of objective function evaluations. See [`ExperimentDataPrior`](@ref).
  * `domain::Domain`: The [`Domain`](@ref) of `x`.
  * `y_max::AbstractVector{<:Real}`: The constraints on `y`. (See the definition above.)

See also: [`bo!`](@ref)
