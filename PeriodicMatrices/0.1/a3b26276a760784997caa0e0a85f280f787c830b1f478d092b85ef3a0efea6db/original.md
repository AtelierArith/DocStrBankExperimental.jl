```
psceigfr(A::FourierFunctionMatrix[, N]; P, atol) -> ce
```

Compute the characteristic exponents of a continuous-time periodic matrix in *Fourier Function Matrix* representation. 

For a given square continuous-time periodic function matrix `A(t)` of period `T`  in a  *Fourier Function Matrix* representation,  the characteristic exponents `ce` are computed as the eigenvalues of the state operator `A(t)-D*I` lying in the  fundamental strip `-ω/2 <  Im(λ) ≤ ω/2`, where `ω = 2π/T`. A finite dimensional truncated matrix of order `n*(2*N*P+1)`  is built to approximate `A(t)-D*I`, where `n` is the order of `A(t)`,  `N` is the number of selected harmonic components in the Fourier representation and `P` is the period multiplication number (default: `P = 1`). The default value used for `N` is `N = max(10,p-1)`, where `p` the number of harmonics terms of `A(t)` (see [`FourierFunctionMatrix`](@ref)). 

The keyword argument `atol` (default: `atol = 1.e-10`) is a tolerance on the magnitude of the trailing components of the  associated eigenvectors used to validate their asymptotic (exponential) decay. Only eigenvalues satisfying this check are returned in `ce`. 
