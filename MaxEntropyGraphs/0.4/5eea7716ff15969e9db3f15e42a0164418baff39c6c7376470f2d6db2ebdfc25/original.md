```
∇L_DBCM_reduced!(∇L::AbstractVector, θ::AbstractVector, k_out::AbstractVector, k_in::AbstractVector, F::AbstractVector, nz_out::Vector, nz_in::Vector, x::AbstractVector, y::AbstractVector,n::Int)
```

Compute the gradient of the log-likelihood of the reduced DBCM model using the exponential formulation in order to maintain convexity.

For the optimisation, this function will be used togenerate an anonymous function associated with a specific model. The function  will update pre-allocated vectors (`∇L`,`x` and `y`) for speed. The gradient is non-allocating.

# Arguments

  * `∇L`: the gradient of the log-likelihood of the reduced model
  * `θ`: the maximum likelihood parameters of the model ([α; β])
  * `k_out`: the reduced outdegree sequence
  * `k_in`: the reduced indegree sequence
  * `F`: the frequency of each pair in the degree sequence
  * `nz_out`: the indices of non-zero elements in the reduced outdegree sequence
  * `nz_in`: the indices of non-zero elements in the reduced indegree sequence
  * `x`: the exponentiated maximum likelihood parameters of the model ( xᵢ = exp(-αᵢ) )
  * `y`: the exponentiated maximum likelihood parameters of the model ( yᵢ = exp(-βᵢ) )
  * `n`: the number of nodes in the reduced model

# Examples

```jldoctest ∇L_DBCM_reduced
# Explicit use with DBCM model:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> ∇L = zeros(Real, length(model.θᵣ));

julia> x  = zeros(Real, length(model.xᵣ));

julia> y  = zeros(Real, length(model.yᵣ));

julia> ∇model_fun! = θ -> ∇L_DBCM_reduced!(∇L, θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, x, y, model.status[:d_unique]);

julia> ∇model_fun!(model.θᵣ);

```

```jldoctest ∇L_DBCM_reduced
# Use within optimisation.jl framework:
julia> fun = (θ,p) -> -L_DBCM_reduced(θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, model.status[:d_unique]);

julia> x  = zeros(Real, length(model.xᵣ)); # initialise  buffer

julia> y  = zeros(Real, length(model.yᵣ));#  initialise  buffer

julia> ∇fun! = (∇L, θ, p) -> ∇L_DBCM_reduced!(∇L, θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, x, y, model.status[:d_unique]);

julia> θ₀ = initial_guess(model); # initial condition

julia> foo = MaxEntropyGraphs.Optimization.OptimizationFunction(fun, grad=∇fun!); # define target function 

julia> prob  = MaxEntropyGraphs.Optimization.OptimizationProblem(foo, θ₀); # define the optimisation problem

julia> method = MaxEntropyGraphs.OptimizationOptimJL.LBFGS(); # set the optimisation method

julia> MaxEntropyGraphs.Optimization.solve(prob, method); # solve it

```
