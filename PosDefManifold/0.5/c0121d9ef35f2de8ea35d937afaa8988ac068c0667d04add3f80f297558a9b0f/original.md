```julia
    procrustes(P::ℍ{T}, Q::ℍ{T}, extremum="min") where T<:RealOrComplex
```

Given two positive definite matrices $P$ and $Q$, return by default the solution of problem

$\textrm{argmin}_Uδ(P,U^HQU)$,

where $U$ varies over the set of unitary matrices and $δ(.,.)$ is a distance or divergence function.

$U^HQU$ is named in physics the *unitary orbit* of $Q$.

If the argument `extremum` is passed as "max", it returns instead the solution of

$\textrm{argmax}_Uδ(P,U^HQU)$.

$P$ and $Q$ must be flagged as `Hermitian`. See [typecasting matrices](@ref).

As it has been shown in Bhatia and Congedo (2019)[🎓](@ref), using each of the [Fisher](@ref), [logdet zero](@ref), [Wasserstein](@ref) and the Kullback-Leibler divergence (see [logdet α](@ref)), the best approximant to $P$ from the unitary orbit of $Q$ commutes with $P$ and, surprisingly, has the same closed-form expression, namely

$U_Q^↓U_P^{↓H}$ for the argmin and $U_Q^↑U_P^{↓H}$ for the argmax,

where $U^↓$ denotes the eigenvector matrix of the subscript argument with eigenvectors in columns sorted by *decreasing* order of corresponding eigenvalues and $U^↑$ denotes the eigenvector matrix of the subscript argument with eigenvectors in columns sorted by *increasing* order of corresponding eigenvalues.

The same solutions are known since a long time also by solving the extremal problem here above using the [Euclidean](@ref) metric (Umeyama, 1988).

The generalized Procrustes problem

$\textrm{argmin}_Usum_{i=1}^{k}δ(P_i,U^HQ_iU)$

can be solved using Julia package [Manopt](https://github.com/kellertuer/Manopt.jl).

**Examples**

```julia
using PosDefManifold
P=randP(3)
Q=randP(3)
# argmin problem
U=procrustes(P, Q)
# argmax problem
V=procrustes(P, Q, "max")
```
