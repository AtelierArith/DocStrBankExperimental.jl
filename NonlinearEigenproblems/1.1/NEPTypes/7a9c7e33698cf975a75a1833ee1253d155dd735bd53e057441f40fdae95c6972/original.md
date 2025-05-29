```
struct PEP <: AbstractSPMF
function PEP(AA::Vector{AbstractMatrix})
```

The type `PEP` defines a polynomial eigenvalue  problem via its monomial coefficients. A polynomial eigenvalue problem (PEP) is defined by the sum the

$$
Σ_i A_i λ^i,
$$

where $i = 0,1,2,$, and  all of the matrices are of size $n×n$. The vector `AA` contains $A_1,...$.

# Example

```julia-repl
julia> A0=[1.0 3; 4 5]; A1=A0.+one(2); A2=ones(2,2);
julia> pep=PEP([A0,A1,A2])
julia> compute_Mder(pep,3)-(A0+A1*3+A2*9)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0
```

See also [`polyeig`](methods.md#NonlinearEigenproblems.NEPSolver.polyeig), [`companion`](methods.md#NonlinearEigenproblems.NEPSolver.companion), [`ChebPEP`](@ref), [`interpolate`](@ref).
