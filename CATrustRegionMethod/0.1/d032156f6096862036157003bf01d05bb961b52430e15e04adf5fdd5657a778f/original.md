phi(g, H, δ, γ*2, r, print*level)                     (3)

The function is a decreasing univariate function in δ. It is equal to -1 when H + δ I >= 0 and ||d*k|| < γ*2 r. 	It is equal to 0 when H + δ I >= 0 and γ*2 r <= ||d*k|| <= r. It is equal to 1 when H + δ I < 0 or ||d*k|| > r. 	With d*k = (H + δ * I) ^ {-1} (-g)

# Inputs:

  * `g::Vector{Float64}`. See (1). The gradient at the current iterate x.
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.

See (1). The Hessian at the current iterate x.

  * `δ::Float64`. See (1). The variable in the function.
  * `γ_2::Float64`. See (2). Specify how close the step d_k should be close from the trust-region boundary when δ > 0.
  * `r::Float64`. See (1). The trsut-region radius.
  * `print_level::Float64`. The verbosity level of logs.

# Outputs:

An integer values that takes the values -1, 0, or 1.
