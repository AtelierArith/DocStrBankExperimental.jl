```
solve_model!(m::DBCM)
```

Compute the likelihood maximising parameters of the DBCM model `m`. 

# Arguments

  * `method::Symbol`: solution method to use, can be `:fixedpoint` (default), or :NelderMead, :BFGS, :LBFGS and :Newton.
  * `initial::Symbol`: initial guess for the parameters $\Theta$, can be :degrees (default), :degrees*minor, :random, :uniform, or :chung*lu.
  * `maxiters::Int`: maximum number of iterations for the solver (defaults to 1000).
  * `verbose::Bool`: set to show log messages (defaults to false).
  * `ftol::Real`: function tolerance for convergence with the fixedpoint method (defaults to 1e-8).
  * `abstol::Union{Number, Nothing}`: absolute function tolerance for convergence with the other methods (defaults to `nothing`).
  * `reltol::Union{Number, Nothing}`: relative function tolerance for convergence with the other methods (defaults to `nothing`).
  * `AD_method::Symbol`: autodiff method to use, can be any of :AutoZygote, :AutoReverseDiff, :AutoForwardDiff and :AutoFiniteDiff. Performance depends on the size of the problem (defaults to `:AutoZygote`),
  * `analytical_gradient::Bool`: set the use the analytical gradient instead of the one generated with autodiff (defaults to `false`)

# Examples

```jldoctest DBCM_solve
# default use
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

```

```jldoctest DBCM_solve
# using analytical gradient and degrees minor initial guess
julia> solve_model!(model, method=:BFGS, analytical_gradient=true, initial=:degrees_minor)
(DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (16 vertices, 15 unique degree pairs, 0.94 compression ratio), retcode: Success
u: [3.118482950362848, 2.2567400402511617, 2.2467332710940333, 0.8596258292464105, 0.4957550197436504, 0.3427782029923598, 0.126564995232929, -0.3127732185244699, -0.3967757456352901, -0.43450987676209596  …  -0.5626916621021604, 1.223396713832784, 0.10977479732876981, -1.0367565290851806, -2.0427364999923148, -0.650376357149203, -1.5165614611776657, 0.7532475835319463, 0.39856890694767605, -0.6704522097652438]
Final objective value:     120.15942408828177
)

```
