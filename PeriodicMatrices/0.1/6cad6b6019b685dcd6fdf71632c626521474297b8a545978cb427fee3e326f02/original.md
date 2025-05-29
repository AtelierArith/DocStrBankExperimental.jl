```
psceighr(Ahr::HarmonicArray[, N]; P, nperiod, shift, atol) -> ce
```

Compute the characteristic exponents of a continuous-time periodic matrix in *Harmonic Array* representation. 

For a given square continuous-time periodic function matrix `Ahr(t)` of period `T`  in a  *Harmonic Array* representation,  the characteristic exponents `ce` are computed as the eigenvalues of a truncated harmonic state operator `A(N)-E(N)` lying in the  fundamental strip `-ω/2 <  Im(λ) ≤ ω/2`, where `ω = 2π/T`. If `Ahr(t)` has the harmonic components `A_0`, `A_1`, ..., `A_p`, then  for `N ≥ p`, `P = 1` and `nperiod = 1`, the matrices `A(N)` and `E(N)` are built as

```
       ( A_0  A_{-1} …  A_{-p}        0    )           ( -im*ϕ_{-N}I                                 0        )
       ( A_1   A_0             ⋱           )           (     ⋮       ⋱                                        )
       (  ⋮         ⋱            ⋱         )           (               -im*ϕ_{-1}*I                           )
A(N) = ( A_p             ⋱          A_{-p} ) , E(N) =  (                           -im*ϕ_{0}*I                )
       (        ⋱           ⋱         ⋮    )           (     ⋮                                  ⋱              )
       (  0        A_p      …         A_0  )           (     0                                   -im*ϕ_{N}I   )
```

with `ϕ_{i} := shift+i*ω`. If `N < p`, then a truncated *full* block Toeplitz matrix A(N) is built using the first `N` harmonic components.  The default value used for `N` is `N = max(10,p-1)`. 

Generally, for given `P ≥ 1` and  `nperiod ≥ 1`, the block Toeplitz matrix `A(N)` (and also `E(N)`) is constructed with `(2N*np+1)×(2N*np+1)` blocks, with `np = P*nperiod`, such that each `A_i` is preceeded in its column by `np-1` zero blocks,  each `A_{-i}` is preceeded in its row by `np-1` zero blocks and all diagonal blocks are equal to`A_0`.  

The keyword argument `atol` (default: `atol = 1.e-10`) is a tolerance on the magnitude of the trailing components of the  associated eigenvectors used to validate their asymptotic (exponential) decay.  Only eigenvalues satisfying this check are returned in `ce`. 

*References*

[1] J. Zhou, T. Hagiwara, and M. Araki.      Spectral characteristics and eigenvalues computation of the harmonic state operators in continuous-time periodic systems.      Systems and Control Letters, 53:141–155, 2004.
