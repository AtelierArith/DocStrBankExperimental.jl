```
struct PartialACA
```

Adaptive cross approximation algorithm with partial pivoting. This structure can be used to generate an [`RkMatrix`](@ref) from a matrix-like object `M` as follows:

```jldoctest
using LinearAlgebra
rtol = 1e-6
comp = PartialACA(;rtol)
A = rand(10,2)
B = rand(10,2)
M = A*adjoint(B) # a low-rank matrix
R = comp(M, axes(M)...) # compress the entire matrix `M`
norm(Matrix(R) - M) < rtol*norm(M) # true

# output

true

```

Because it uses partial pivoting, the linear operator does not have to be evaluated at every `i,j`. This is usually much faster than [`TSVD`](@ref), but due to the pivoting strategy the algorithm may fail in special cases, even when the underlying linear operator is of low rank.
