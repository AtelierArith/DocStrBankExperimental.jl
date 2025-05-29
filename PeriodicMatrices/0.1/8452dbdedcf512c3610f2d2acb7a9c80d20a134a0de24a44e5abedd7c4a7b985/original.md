```
 pseig(A, K = 1; lifting = false, solver, reltol, abstol, dt) -> cm
```

Compute the characteristic multipliers of a continuous-time periodic matrix. 

For the given square periodic matrix `A(t)` of period `T`,  the characteristic multipliers `cm` are the eigenvalues of  the monodromy matrix `Ψ = Φ(T,0)`, where `Φ(t,τ)` is the state transition matrix satisfying the homogeneous linear ODE 

```
dΦ(t,τ)/dt = A(t)Φ(t,τ),  Φ(τ,τ) = I.
```

If `lifting = false`, `Ψ` is computed as a product of `K` state transition matrices  `Ψ = Ψ_K*...*Ψ_1` (see [`monodromy`](@ref) with the associated keyword arguments).  The eigenvalues are computed using the periodic Schur decomposition method of [1]. `A` may be given as a [`PeriodicFunctionMatrix`](@ref), a [`HarmonicArray`](@ref), a [`PeriodicSymbolicMatrix`](@ref) or a  [`FourierFunctionMatrix`](@ref). 

If `lifting = true`, `Ψ` is (implicitly) expressed as `Ψ = inv(N)*M`, where `M-λN` is a regular pencil with `N` invertible and   the eigenvalues of `M-λN` are the same as those of the matrix product `Ψ := Ψ_K*...*Ψ_1`.  An efficient version of the structure exploiting fast reduction method of [2] is employed,  which embeds the determination of transition matrices into the reduction algorithm.  This option may occasionally lead to inaccurate results for large values of `K`. 

*References*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
