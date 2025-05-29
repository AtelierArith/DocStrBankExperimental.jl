```
solve_model!(m::BiCM)
```

Compute the likelihood maximising parameters of the BiCM model `m`. 

# Arguments

  * `method::Symbol`: solution method to use, can be `:fixedpoint` (default), or :NelderMead, :BFGS, :LBFGS and :Newton.
  * `initial::Symbol`: initial guess for the parameters $\Theta$, can be :degrees (default), :random, :uniform, or :chung_lu.
  * `maxiters::Int`: maximum number of iterations for the solver (defaults to 1000).
  * `verbose::Bool`: set to show log messages (defaults to false).
  * `ftol::Real`: function tolerance for convergence with the fixedpoint method (defaults to 1e-8).
  * `abstol::Union{Number, Nothing}`: absolute function tolerance for convergence with the other methods (defaults to `nothing`).
  * `reltol::Union{Number, Nothing}`: relative function tolerance for convergence with the other methods (defaults to `nothing`).
  * `AD_method::Symbol`: autodiff method to use, can be any of :AutoZygote, :AutoReverseDiff, :AutoForwardDiff and :AutoFiniteDiff. Performance depends on the size of the problem (defaults to `:AutoZygote`),
  * `analytical_gradient::Bool`: set the use the analytical gradient instead of the one generated with autodiff (defaults to `false`)

# Examples

```jldoctest BiCM_solve
# default use
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

```

```jldoctest BiCM_solve
# using analytical gradient and uniform initial guess
julia> solve_model!(model, method=:BFGS, analytical_gradient=true, initial=:uniform)
(BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (25 + 15 vertices, 6 + 6 unique degrees, 0.30 compression ratio), retcode: Success
u: [1.449571644621672, 0.8231752829683303, 0.34755085972479766, -0.04834480708852856, -0.3984299800917503, -0.7223268299919358, 1.6090554004279671, 1.2614196476197532, 0.9762560461922147, 0.11406188481061938, -0.24499004480426345, -2.2646067641037333]
Final objective value:     171.15095803718134
)

```
