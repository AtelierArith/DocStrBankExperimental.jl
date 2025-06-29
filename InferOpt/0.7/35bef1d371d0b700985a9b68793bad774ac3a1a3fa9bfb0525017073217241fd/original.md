```
RegularizedFrankWolfe <: AbstractRegularized
```

Regularized optimization layer which relies on the Frank-Wolfe algorithm to define a probability distribution while solving

```
ŷ(θ) = argmax_{y ∈ C} {θᵀy - Ω(y)}
```

!!! warning
    Since this is a conditional dependency, you need to have loaded the following packages before using `RegularizedFrankWolfe`:

      * `DifferentiableFrankWolfe.jl`
      * `FrankWolfe.jl`
      * `ImplicitDifferentiation.jl`


# Fields

  * `linear_maximizer`: linear maximization oracle `θ -> argmax_{x ∈ C} θᵀx`, implicitly defines the polytope `C`
  * `Ω`: regularization function `Ω(y)`
  * `Ω_grad`: gradient function of the regularization function `∇Ω(y)`
  * `frank_wolfe_kwargs`: named tuple of keyword arguments passed to the Frank-Wolfe algorithm
  * `implicit_kwargs`: named tuple of keyword arguments passed to the implicit differentiation algorithm (in particular, the needed linear solver)

# Frank-Wolfe parameters

Some values you can tune:

  * `epsilon::Float64`: precision target
  * `max_iteration::Integer`: max number of iterations
  * `timeout::Float64`: max runtime in seconds
  * `lazy::Bool`: caching strategy
  * `away_steps::Bool`: avoid zig-zagging
  * `line_search::FrankWolfe.LineSearchMethod`: step size selection
  * `verbose::Bool`: console output

See the documentation of FrankWolfe.jl for details.
