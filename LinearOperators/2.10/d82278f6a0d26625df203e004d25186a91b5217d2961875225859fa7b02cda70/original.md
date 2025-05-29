solve*shifted*system!(x, B,  b, σ)

Solve linear system (B + σI) x = b, where B is a forward L-BFGS operator and σ ≥ 0.

### Parameters

  * `x::AbstractVector{T}`: preallocated vector of length n that is used to store the solution x.
  * `B::LBFGSOperator`: forward L-BFGS operator that models a matrix of size n x n.
  * `b::AbstractVector{T}`: right-hand side vector of length n.
  * `σ::T`: nonnegative shift.

### Returns

  * `x::AbstractVector{T}`: solution vector `x` of length n.

### Method

The method uses a two-loop recursion-like approach with modifications to handle the shift `σ`.

### Example

```julia
using Random

# Problem setup
n = 100  # size of the problem
mem = 10   # L-BFGS memory size
scaling = true  # enable scaling

# Create an L-BFGS operator
B = LBFGSOperator(n, mem = mem, scaling = scaling)

# Add random {s, y} pairs to the L-BFGS operator
for _ = 1:10
    s = rand(n)   
    y = rand(n)   
    push!(B, s, y)  # Add the {s, y} pair to B
end

# Prepare vectors for the system
x = zeros(n)   # Preallocated solution vector
b = rand(n)        # Right-hand side vector
σ = 0.1            # Small shift value

# Solve the shifted system
result = solve_shifted_system!(x, B, b, σ)

# Check that the solution is close enough (residual test)
@assert norm(B * x + σ * x - b) / norm(b) < 1e-8
```

### References

Erway, J. B., Jain, V., & Marcia, R. F. Shifted L-BFGS Systems. Optimization Methods and Software, 29(5), pp. 992-1004, 2014.
