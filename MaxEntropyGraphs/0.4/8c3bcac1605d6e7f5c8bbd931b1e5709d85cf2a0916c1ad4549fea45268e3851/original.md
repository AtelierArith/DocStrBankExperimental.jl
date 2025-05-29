```
solve_model!(m::UBCM; kwargs...)
```

Compute the likelihood maximising parameters of the UBCM model `m`. 

# Arguments

  * `method::Symbol`: solution method to use, can be `:fixedpoint` (default), or :NelderMead, :BFGS, :LBFGS and :Newton.
  * `initial::Symbol`: initial guess for the parameters $\Theta$, can be :degrees, :degrees*minor, :random, :uniform, or :chung*lu.
  * `maxiters::Int`: maximum number of iterations for the solver (defaults to 1000).
  * `verbose::Bool`: set to show log messages (defaults to false).
  * `ftol::Real`: function tolerance for convergence with the fixedpoint method (defaults to 1e-8).
  * `abstol::Union{Number, Nothing}`: absolute function tolerance for convergence with the other methods (defaults to `nothing`).
  * `reltol::Union{Number, Nothing}`: relative function tolerance for convergence with the other methods (defaults to `nothing`).
  * `AD_method::Symbol`: autodiff method to use, can be any of :AutoZygote, :AutoReverseDiff, :AutoForwardDiff and :AutoFiniteDiff. Performance depends on the size of the problem (defaults to `:AutoZygote`),
  * `analytical_gradient::Bool`: set the use the analytical gradient instead of the one generated with autodiff (defaults to `false`)

# Examples

```jldoctest UBCM_solve
# default use
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

```

```jldoctest UBCM_solve
# using analytical gradient and degrees minor initial guess
julia> solve_model!(model, method=:BFGS, analytical_gradient=true, initial=:degrees_minor)
(UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (34 vertices, 11 unique degrees, 0.32 compression ratio), retcode: Success
u: [2.851659905903854, 2.053008374573552, 1.5432639513870743, 1.152360118212239, 0.8271267490690292, 0.5445045274064909, -0.1398726818076551, -0.3293252270659469, -0.6706207459338859, -1.2685575582149227, -1.410096540372487]
Final objective value:     168.68325136302835
)

```

See also: [`initial_guess`](@ref MaxEntropyGraphs.initial_guess(::UBCM)), [`∇L_UBCM_reduced!`](@ref MaxEntropyGraphs.∇L_UBCM_reduced!)
