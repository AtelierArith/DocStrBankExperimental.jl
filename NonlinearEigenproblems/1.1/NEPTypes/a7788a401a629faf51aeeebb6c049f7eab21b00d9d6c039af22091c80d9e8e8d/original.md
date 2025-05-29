```
type DEP <: AbstractSPMF
function DEP(AA::Vector{AbstractMatrix} [,tauv::Vector=[0,1.0]])
```

A `DEP` (Delay Eigenvalue problem) is a problem defined by the sum

$$
M(λ)=-λI + Σ_i A_i exp(-τ_i λ)
$$

where all of the matrices are of size $n×n$. This type of NEP describes the stability of time-delay systems.

The construction takes the system matrices $A_i$, and `tauv` is a vector of the values  $τ_i$.

# Example:

```julia-repl
julia> A0=randn(3,3); A1=randn(3,3);
julia> tauv=[0,0.2] # Vector with delays
julia> dep=DEP([A0,A1],tauv)
julia> λ=3.0;
julia> M1=compute_Mder(dep,λ)
julia> M2=-λ*I+A0+A1*exp(-tauv[2]*λ)
julia> norm(M1-M2)
0.0
```
