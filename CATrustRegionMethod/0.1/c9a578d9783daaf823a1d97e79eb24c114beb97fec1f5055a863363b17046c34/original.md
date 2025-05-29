compute*ρ*hat(fval*current, fval*next, gval*current, gval*next, hessian*current, d*k, θ, print_level)

Computes ρ*hat based on our approach: the ratio of the actual reduction in the objective function to the predicted reduction based   on the second-order Taylor series expansion.   ρ*hat = (fval*next - fval*current) / (-M*k + 0.5 * θ * min(||gval*current||, ||gval*next||) * ||d*k||)   where M_k = 1/2 d ^ T * H * d + g ^ T  * d

# Inputs:

```
- `fval_current::Float64`. The function value at the current iterate x_k.
- `fval_next::Float64`. The function value at the next candidate iterate x_k + d_k.
- `gval_current::Vector{Float64}`. The gradient at the current iterate x_k.
- `gval_next::Vector{Float64}`. The gradient at the next candidate iterate x_k + d_k.
- `hessian_current::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.
	The Hessian at the current iterate x_k.
- `d_k::Vector{Float64}`. The serach direction.
- `θ::Float64`. Param used for the preducted reduction.
- `print_level::Float64`. The verbosity level of logs.
```

# Output:

Scalar that represents the value of the ratio of the actual reduction in the objective function to the predicted    reduction based on the second-order Taylor series expansion.
