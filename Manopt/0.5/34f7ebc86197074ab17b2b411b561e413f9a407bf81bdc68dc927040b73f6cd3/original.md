```
ManifoldCountObjective{E,P,O<:AbstractManifoldObjective,I<:Integer} <: AbstractDecoratedManifoldObjective{E,P}
```

A wrapper for any [`AbstractManifoldObjective`](@ref) of type `O` to count different calls to parts of the objective.

# Fields

  * `counts` a dictionary of symbols mapping to integers keeping the counted values
  * `objective` the wrapped objective

# Supported symbols

| Symbol                       | Counts calls to (incl. `!` variants)   | Comment                              |
|:---------------------------- |:-------------------------------------- |:------------------------------------ |
| `:Cost`                      | [`get_cost`](@ref)                     |                                      |
| `:EqualityConstraint`        | [`get_equality_constraint`](@ref)      | requires vector of counters          |
| `:EqualityConstraints`       | [`get_equality_constraint`](@ref)      | when evaluating all of them with `:` |
| `:GradEqualityConstraint`    | [`get_grad_equality_constraint`](@ref) | requires vector of counters          |
| `:GradEqualityConstraints`   | [`get_grad_equality_constraint`](@ref) | when evaluating all of them with `:` |
| `:GradInequalityConstraint`  | [`get_inequality_constraint`](@ref)    | requires vector of counters          |
| `:GradInequalityConstraints` | [`get_inequality_constraint`](@ref)    | when evaluating all of them with `:` |
| `:Gradient`                  | [`get_gradient`](@ref)`(M,p)`          |                                      |
| `:Hessian`                   | [`get_hessian`](@ref)                  |                                      |
| `:InequalityConstraint`      | [`get_inequality_constraint`](@ref)    | requires vector of counters          |
| `:InequalityConstraints`     | [`get_inequality_constraint`](@ref)    | when evaluating all of them with `:` |
| `:Preconditioner`            | [`get_preconditioner`](@ref)           |                                      |
| `:ProximalMap`               | [`get_proximal_map`](@ref)             |                                      |
| `:StochasticGradients`       | [`get_gradients`](@ref)                |                                      |
| `:StochasticGradient`        | [`get_gradient`](@ref)`(M, p, i)`      |                                      |
| `:SubGradient`               | [`get_subgradient`](@ref)              |                                      |
| `:SubtrahendGradient`        | [`get_subtrahend_gradient`](@ref)      |                                      |

# Constructors

```
ManifoldCountObjective(objective::AbstractManifoldObjective, counts::Dict{Symbol, <:Integer})
```

Initialise the `ManifoldCountObjective` to wrap `objective` initializing the set of counts

```
ManifoldCountObjective(M::AbstractManifold, objective::AbstractManifoldObjective, count::AbstractVecor{Symbol}, init=0)
```

Count function calls on `objective` using the symbols in `count` initialising all entries to `init`.
