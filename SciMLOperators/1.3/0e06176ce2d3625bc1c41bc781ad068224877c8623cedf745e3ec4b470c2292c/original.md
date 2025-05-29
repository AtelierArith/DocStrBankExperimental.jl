Computes the lazy pairwise Kronecker product, or tensor product, operator of `AbstractMatrix`, and `AbstractSciMLOperator` subtypes. Calling `⊗(ops...)` is equivalent to `Base.kron(ops...)`. Fast operator evaluation is performed without forming the full tensor product operator.

```
TensorProductOperator(A, B) = A ⊗ B
TensorProductOperator(A, B, C) = A ⊗ B ⊗ C

(A ⊗ B)(v) = vec(B * reshape(v, M, N) * transpose(A))
```

where `M = size(B, 2)`, and `N = size(A, 2)`

# Example

```
using SciMLOperators, LinearAlgebra

# Create basic operators
A = rand(3, 3)
B = rand(4, 4)
A_op = MatrixOperator(A)
B_op = MatrixOperator(B)

# Create tensor product operator
T = A_op ⊗ B_op

# Apply to a vector using the new interface
v = rand(3*4)    # Action vector
u = rand(3*4)    # Update vector
p = nothing
t = 0.0

# Out-of-place application
result = T(v, u, p, t)

# For in-place operations, need to cache the operator first
T_cached = cache_operator(T, v)

# In-place application
w = zeros(size(T, 1))
T_cached(w, v, u, p, t)

# In-place with scaling
w_orig = copy(w)
α = 2.0
β = 0.5
T_cached(w, v, u, p, t, α, β) # w = α*(T*v) + β*w_orig
```
