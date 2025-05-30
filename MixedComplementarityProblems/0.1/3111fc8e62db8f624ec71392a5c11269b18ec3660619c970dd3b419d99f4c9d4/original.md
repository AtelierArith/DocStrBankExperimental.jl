Basic interior point solver, based on Nocedal & Wright, ch. 19. Computes step directions `δz` by solving the relaxed primal-dual system, i.e.                          ∇F(z; ϵ) δz = -F(z; ϵ).

Given a step direction `δz`, performs a "fraction to the boundary" linesearch, i.e., for `(x, s)` it chooses step size `α_s` such that               α*s = max(α ∈ [0, 1] : s + α δs ≥ (1 - τ) s) and for `y` it chooses step size `α*s` such that               α_y = max(α ∈ [0, 1] : y + α δy ≥ (1 - τ) y).

A typical value of τ is 0.995. Once we converge to ||F(z; psilon)|| ≤ ϵ, we typically decrease ϵ by a factor of 0.1 or 0.2, with smaller values chosen when the previous subproblem is solved in fewer iterations.

Positional arguments:     - `mcp::PrimalDualMCP`: the mixed complementarity problem to solve.     - `θ::AbstractVector{<:Real}`: the parameter vector.

Keyword arguments:     - `x₀::AbstractVector{<:Real}`: the initial primal variable.     - `y₀::AbstractVector{<:Real}`: the initial dual variable.     - `s₀::AbstractVector{<:Real}`: the initial slack variable.     - `ϵ₀::Real`: the initial relaxation scale.     - `tol::Real = 1e-4`: the tolerance for the KKT error.     - `max_inner_iters::Int = 20`: the maximum number of inner iterations.     - `max_outer_iters::Int = 50`: the maximum number of outer iterations.     - `tightening_rate::Real = 0.1`: the rate at which to tighten the tolerance.     - `loosening_rate::Real = 0.5`: the rate at which to loosen the tolerance.     - `min_stepsize::Real = 1e-2`: the minimum step size for the linesearch.     - `verbose::Bool = false`: whether to print debug information.     - `linear_solve_algorithm::LinearSolve.SciMLLinearSolveAlgorithm`: the linear solve algorithm to use. Any solver from `LinearSolve.jl` can be used.
