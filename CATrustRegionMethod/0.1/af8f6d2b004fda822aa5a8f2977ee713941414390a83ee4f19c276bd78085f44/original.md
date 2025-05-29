optimizeSecondOrderModel(problem*name, g, H, δ, γ*1, γ*2, γ*3, r, min*grad, print*level) This function finds a solution to the quadratic problem

```
argmin_d 1/2 d ^ T * H * d + g ^ T  * d
s.t. || d || <= r                  (1)
where || . || is the l2 norm of a vector.
```

This problem (1) is solved approximately by solving the follwoing system of equations:

||H d*k + g + δ d*k|| <= γ*1 * min*grad           (2) γ*2 * ||d*k||) <=  γ*2 * r ||d*k|| <= r M*k(d*k) <= - γ*3 * 0.5 * δ * ||d*k|| ^ 2 H + δ I ≥ 0

The logic to find the solution either by defining a univariate function ϕ (See (3)) in δ. Then, we construct an interval [δ, δ*prime] 	such that ϕ(δ) * ϕ(δ*prime) <= 0 and then using bisection, we find a root δ*m for the ϕ function. Using δ*m 	we compute d*k as d*k = (H + δ_m * I) ^ {-1} (-g). If for a reason, we failed to construct the interval or the bisection failed, 	then we mark the problem as a hard case and we use inverse power iteration to find an approximate minimum eigen value 	of the Hessian and then compute the search direction using the minimum eigen value.

# Inputs:

  * `problem_name::String`. Name of the problem being optimized for example a CUTEst benchamrk problem SCURLY10.
  * `g::Vector{Float64}`. See (1). The gradient at the current iterate x.
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.

See (1). The Hessian at the current iterate x.

  * `δ::Float64`. See (1). A warm start value for solving the above system (2)
  * `γ_1::Float64`. See (2). Specify how much the step d_k should be close from the exact solution.
  * `γ_2::Float64`. See (2). Specify how close the step d_k should be close from the trust-region boundary when δ > 0.
  * `γ_3::Float64`. See (2). Specify how much reduction in the model relative to the norm of the search direction.
  * `r::Float64`. See (1). The trsut-region radius.
  * `min_grad::Float64`. See (2). The minumum gradient over all iterates.
  * `print_level::Float64`. The verbosity level of logs.

# Outputs:

'success*subproblem*solve::Bool'   'δ*k::Float64'.  See (1), (2), and (3). The solution of the above system of equations such that ϕ(δ*k) = 0.   This is used to compute d*k.   'd*k::Vector{Float64}`. See (1). The search direction which is the solution of (1).   'temp*total*number*factorizations::Int64'. The total number of choelsky factorization done for H + δ I.   'hard*case::Bool'. See (2). It specifies if δ*k = -λ*1(H) where λ*1 is the minimum eigenvalue of the matrix H.   'temp*total*number*factorizations*findinterval::Int64'. The number of choelsky factorization done for H + δ I when finding the interval [δ, δ*prime].   'temp*total*number*factorizations*bisection::Int64'. The number of choelsky factorization done for H + δ I when doing the bisection.   'total*number*factorizations*compute*search*direction::Int64'. The number of choelsky factorization done when computing d*k = (H + δ*m * I) ^ {-1} (-g)   'temp*total*number*factorizations*inverse*power*iteration::Int64'. The number of choelsky factorization done when solving the hard case instance.   temp*total*number*factorizations = temp*total*number*factorizations*findinterval

  * temp*total*number*factorizations*bisection + total*number*factorizations*compute*search_direction
  * temp*total*number*factorizations*inverse*power*iteration
