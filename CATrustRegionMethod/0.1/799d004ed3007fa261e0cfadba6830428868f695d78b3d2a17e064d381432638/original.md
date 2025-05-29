computeSecondOrderModel(g, hessian_current,d)   Computes the second-order Taylor series expansion around the current iterate:   	1/2 d ^ T * H * d + g ^ T  * d (1)

# Inputs:

```
- `g::Vector{Float64}`. The gradient at the current iterate x.
- `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`.
	The Hessian at the current iterate x.
- `d::Vector{Float64}`. The serach direction.
```

# Output:

Scalar that represents the value of the second-order Taylor series expansion around the current iterate.
