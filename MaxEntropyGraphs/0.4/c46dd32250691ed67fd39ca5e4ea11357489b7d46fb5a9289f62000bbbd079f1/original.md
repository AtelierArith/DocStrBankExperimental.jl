```
UBCM_reduced_iter!(θ, K, F, x, G)
```

Computer the next fixed-point iteration for the UBCM model using the exponential formulation in order to maintain convexity. The function will update pre-allocated vectors (`G` and `x`) for speed.

# Arguments

  * `θ`: the maximum likelihood parameters of the model
  * `K`: the reduced degree sequence
  * `F`: the frequency of each degree in the degree sequence
  * `x`: the exponentiated maximum likelihood parameters of the model ( xᵢ = exp(-θᵢ) ) (pre-allocated)
  * `G`: the next fixed-point iteration for the UBCM model (pre-allocated)

# Examples

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> G = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> x = zeros(eltype(model.θᵣ), length(model.θᵣ));

julia> UBCM_FP! = θ -> UBCM_reduced_iter!(θ, model.dᵣ, model.f, x, G);

julia> UBCM_FP!(initial_guess(model));

```
