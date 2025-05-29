```
kron(A::LinearMap, B::LinearMap)::KroneckerMap
kron(A, B, Cs...)::KroneckerMap
```

Construct a (lazy) representation of the Kronecker product `A⊗B`. One of the two factors can be an `AbstractMatrix`, which is then promoted to a `LinearMap` automatically.

To avoid fallback to the generic [`Base.kron`](@ref) in the multi-map case, there must be a `LinearMap` object among the first 8 arguments in usage like `kron(A, B, Cs...)`.

For convenience, one can also use `A ⊗ B` or `⊗(A, B, Cs...)` (typed as `\otimes+TAB`) to construct the `KroneckerMap`, even when all arguments are of `AbstractMatrix` type.

If `A`, `B`, `C` and `D` are linear maps of such size that one can form the matrix products `A*C` and `B*D`, then the mixed-product property `(A⊗B)*(C⊗D) = (A*C)⊗(B*D)` holds. Upon vector multiplication, this rule is checked for applicability.

# Examples

```jldoctest; setup=(using LinearAlgebra, SparseArrays, LinearMaps)
julia> J = LinearMap(I, 2) # 2×2 identity map
2×2 LinearMaps.UniformScalingMap{Bool} with scaling factor: true

julia> E = spdiagm(-1 => trues(1)); D = E + E' - 2I;

julia> Δ = kron(D, J) + kron(J, D); # discrete 2D-Laplace operator

julia> Matrix(Δ)
4×4 Matrix{Int64}:
 -4   1   1   0
  1  -4   0   1
  1   0  -4   1
  0   1   1  -4
```
