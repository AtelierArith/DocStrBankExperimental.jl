findinterval(g, H, δ, γ*2, r, print*level)

Constructs an interval [δ, δ*prime] based on the univariate function ϕ (See (3)) such that ϕ(δ) >= 0 and ϕ(δ*prime) <=0.

# Inputs:

  * `g::Vector{Float64}`. See (1). The gradient at the current iterate x.
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.

See (1). The Hessian at the current iterate x.

  * `δ::Float64`. See (1). A warm start value for solving the above system (2).
  * `γ_2::Float64`. See (2). Specify how close the step d_k should be close from the trust-region boundary when δ > 0.
  * `r::Float64`. See (1). The trsut-region radius.
  * `print_level::Float64`. The verbosity level of logs.

# Outputs:

'success*find*interval::Bool'. See (3). It specifies if we found an interval [δ, δ*prime] such that ϕ(δ) * ϕ(δ*prime) <= 0.   'δ::Float64'. See (3). The lower bound of the interval [δ, δ*prime] such that ϕ(δ) >= 0.   'δ*prime::Float64'. See (3). The upper bound of the interval [δ, δ*prime] such that ϕ(δ) <= 0.   'd*δ*prime:Vector{Float64}`. See (1). The search direction which is computed using δ*prime.   'temp*total*number*factorizations*findinterval::Int64'. The number of choelsky factorization done for H + δ I when finding the interval [δ, δ_prime].
