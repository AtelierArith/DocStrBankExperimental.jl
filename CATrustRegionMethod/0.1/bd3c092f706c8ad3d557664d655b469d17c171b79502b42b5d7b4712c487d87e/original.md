bisection(problem*name, g, H, δ, γ*1, γ*2, δ*prime, d*δ*prime, r, min*grad, print*level)

Constructs an interval [δ, δ*prime] based on the univariate function ϕ (See (3)) such that ϕ(δ) >= 0 and ϕ(δ*prime) <=0.

# Inputs:

  * `problem_name::String`. Name of the problem being optimized for example a CUTEst benchamrk problem SCURLY10.
  * `g::Vector{Float64}`. See (1). The gradient at the current iterate x.
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.

See (1). The Hessian at the current iterate x.

  * 'δ::Float64'. See (3). The lower bound of the interval [δ, δ_prime] such that ϕ(δ) >= 0.
  * `γ_1::Float64`. See (2). Specify how much the step d_k should be close from the exact solution.
  * `γ_2::Float64`. See (2). Specify how close the step d_k should be close from the trust-region boundary when δ > 0.
  * 'δ*prime::Float64'. See (3). The upper bound of the interval [δ, δ*prime] such that ϕ(δ) <= 0.
  * 'd*δ*prime:Vector{Float64}`. See (1). The search direction which is computed using δ_prime.
  * `r::Float64`. See (1). The trsut-region radius.
  * `min_grad::Float64`. See (2). The minumum gradient over all iterates.
  * `print_level::Float64`. The verbosity level of logs.

# Outputs:

'success*bisectionl::Bool'. See (3). It specifies if we found δ*m ∈ the interval [δ, δ*prime] such that ϕ(δ*m) = 0.   'δ*m::Float64'. See (1), (2), and (3). The solution of the above system of equations such that ϕ(δ*m) = 0.   'δ::Float64'. See (3). The new lower bound of the interval [δ, δ*prime] such that ϕ(δ) >= 0.   'δ*prime::Float64'. See (3). The new upper bound of the interval [δ, δ*prime] such that ϕ(δ) <= 0.   'd*k:Vector{Float64}`. See (1). The search direction which is the solution of (1).   'temp*total*number*factorizations*bisection::Int64'. The number of choelsky factorization done for H + δ I when doing the bisection.
