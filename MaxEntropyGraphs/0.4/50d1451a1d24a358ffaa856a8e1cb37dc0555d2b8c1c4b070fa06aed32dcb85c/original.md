```
∇L_UBCM_reduced!(∇L::Vector, θ::Vector, K::Vector, F::Vector, x::Vector)
```

Compute the gradient of the log-likelihood of the reduced UBCM model using the exponential formulation (to maintain convexity).

For the optimisation, this function will be used togenerate an anonymous function associated with a specific model.  The gradient is non-allocating and will update pre-allocated vectors (`∇L` and `x`) for speed. 

# Arguments

  * `∇L`: the gradient of the log-likelihood of the reduced model
  * `θ`: the maximum likelihood parameters of the model
  * `K`: the reduced degree sequence
  * `F`: the frequency of each degree in the degree sequence
  * `x`: the exponentiated maximum likelihood parameters of the model ( xᵢ = exp(-θᵢ) )

# Examples

```jldoctest
# Explicit use with UBCM model:
julia> G = MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> ∇L = zeros(Real, length(model.θᵣ));

julia> x  = zeros(Real, length(model.θᵣ));

julia> ∇model_fun! = θ -> ∇L_UBCM_reduced!(∇L, θ, model.dᵣ, model.f, x);

julia> ∇model_fun!(model.θᵣ);

```

```jldoctest
# Use within optimisation.jl framework:
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> fun =  (θ, p) ->  - L_UBCM_reduced(θ, model.dᵣ, model.f);

julia> x  = zeros(Real, length(model.θᵣ)); # initialise gradient buffer

julia> ∇fun! = (∇L, θ, p) -> ∇L_UBCM_reduced!(∇L, θ, model.dᵣ, model.f, x); # define gradient

julia> θ₀ = initial_guess(model); # initial condition

julia> foo = MaxEntropyGraphs.Optimization.OptimizationFunction(fun, grad=∇fun!); # define target function 

julia> prob  = MaxEntropyGraphs.Optimization.OptimizationProblem(foo, θ₀); # define the optimisation problem

julia> method = MaxEntropyGraphs.OptimizationOptimJL.LBFGS(); # set the optimisation method

julia> MaxEntropyGraphs.Optimization.solve(prob, method); # solve it

```
