```
gsdec(sys; job = "finite", prescale, smarg, fast = true,  
      atol = 0,  atol1 = atol, atol2 = atol, rtol = nϵ) -> (sys1, sys2)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`, the additive spectral decomposition `G(λ) = G1(λ) + G2(λ)` such that `G1(λ)`,  the transfer function matrix of the descriptor system `sys1 = (A1-λE1,B1,C1,D1)`,  has only poles in a certain domain of interest `Cg` of the complex plane and `G2(λ)`,  the transfer function matrix of the descriptor system `sys2 = (A2-λE2,B2,C2,0)`, has only poles outside of `Cg`. 

If `prescale = true`, a preliminary balancing of the descriptor system pair `(A,E)` is performed. The default setting is `prescale = MatrixPencils.balqual(sys.A,sys.E) > 10000`,  where the function `pbalqual` from the [MatrixPencils](https://github.com/andreasvarga/MatrixPencils.jl)  package evaluates the scaling quality of the linear pencil `A-λE`. 

The keyword argument `smarg`, if provided, specifies the stability margin for the stable eigenvalues of `A-λE`, such that, in the continuous-time case,  the stable eigenvalues have real parts less than or equal to `smarg`, and in the discrete-time case, the stable eigenvalues have moduli less than or equal to `smarg`. If `smarg = missing`, the used default values  are: `smarg = -sqrt(ϵ)`, for a continuous-time system, and `smarg = 1-sqrt(ϵ)`,  for a discrete-time system), where `ϵ` is the machine precision of the working accuracy. 

The keyword argument `job`, in conjunction with `smarg`, defines the domain of  interest `Cg`, as follows:

for `job = "finite"`, `Cg` is the whole complex plane without the point at infinity, and     `sys1` has only finite poles and `sys2` has only infinite poles (default);     the resulting `A2` is nonsingular and upper triangular, while the    resulting `E2` is nilpotent and upper triangular;   

for `job = "infinite"`, `Cg` is the point at infinity, and     `sys1` has only infinite poles and `sys2` has only finite poles and     is the strictly proper part of `sys`;     the resulting `A1` is nonsingular and upper triangular, while the    resulting `E1` is nilpotent and upper triangular;   

for `job = "stable"`, `Cg` is the stability domain of eigenvalues defined by `smarg`, and       `sys1` has only stable poles and `sys2` has only unstable and infinite poles;         the resulting pairs `(A1,E1)` and `(A2,E2)` are in generalized Schur form with     `E1` upper triangular and nonsingular and `E2` upper triangular;   

for `job = "unstable"`, `Cg` is the complement of the stability domain of the      eigenvalues defined by `smarg`, and       `sys1` has only unstable and infinite poles and `sys2` has only stable poles;         the resulting pairs `(A1,E1)` and `(A2,E2)` are in generalized Schur form with     `E1` upper triangular and `E2` upper triangular  and nonsingular.   

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance  for the nonzero elements of `A` and `E`. The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The separation of the finite and infinite eigenvalues is performed using  rank decisions based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.
