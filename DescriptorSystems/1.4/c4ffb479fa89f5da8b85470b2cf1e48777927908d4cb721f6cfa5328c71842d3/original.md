```
glsol(sysg, sysf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

Determine for the descriptor systems `sysg = (Ag-λEg,Bg,Cg,Dg)` and  `sysf = (Af-λEf,Bf,Cf,Df)` with the transfer function matrices `G(λ)` and `F(λ)`,  respectively, the descriptor system `sysx` with the transfer function matrix `X(λ)`  such that `X(λ)` is the solution of the linear rational equation

```
X(λ)G(λ) = F(λ) .      (1)
```

If `solgen = true`, the descriptor system `sysgen` is determined representing a generator of  all solutions of (1). Its transfer function matrix has the form `GEN(λ) = [ X0(λ); XN(λ) ]`,  such that any `X(λ)` can be generated as

```
X(λ) = X0(λ) + Z(λ)*XN(λ) ,
```

where `X0(λ)` is a particular solution satisfying `X0(λ)G(λ) = F(λ)`,  `XN(λ)` is a proper rational left nullspace basis of `G(λ)` satisfying `XN(λ)G(λ) = 0`, and  `Z(λ)` is an arbitrary rational matrix with suitable dimensions. If `solgen = false`, `sysgen` is set to `nothing`. 

The call with

```
glsol(sysgf, pf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

uses the compound descriptor system `sysgf = (A-λE,B,[Cg; Cf],[Dg; Df])`,  where `Cf` has `pf` rows, to define   the descriptor systems `sysg = (A-λE,B,Cg,Dg)` and `sysf = (A-λE,B,Cf,Df)` (i.e., `Ag-λEg = Af-λEf = A-λE` and `Bg = Bf = B`). 

The generator `sysgen` has a descriptor system realization `sysgen = (A0-λE0,B0, [C0; CN],[D0; DN])`, which is usually not minimal  (unobservable and/or non-dynamic modes present), with  

```
             ( Ai-λEi    *       *    )  
   A0-λE0  = (   0     Af-λEf    *    ) , 
             (   0       0     Al-λEl ) 

             ( *  )
       B0  = ( *  ),   ( C0 )  = ( C1 C2 C3 ) 
             ( Bl )    ( CN )    ( 0  0  Cl )
```

with `El`, `Ef` and `Ai` invertible and upper triangular, `Ei` nillpotent and upper triangular, and `DN` full column rank. The dimensions of the diagonal blocks of `A0-λE0` are  returned in the named tuple `info` as the components `info.nf`, `info.ninf` and `info.nl`, respectively. 

A minimal order descriptor system realization of the proper basis `XN(λ)` is `(Al-λEl,Bl,Cl,DN)`,  where `Cl` and `DN` have `pr` columns (returned in `info.pr`), representing the dimension of the  left nullspace basis. The normal rank `nrank` of  `G(λ)` is returned in `info.nrank`. 

If `mindeg = false`, the solution `sysx` is determined in the form `sysx = (A0+F*CN-λE0,B0+F*DN,C0,D0)`, where the matrix `F = 0`, unless a nonzero stabilizing gain is used such that `Al+F*Bl-λEl` has stable eigenvalues.  The vector `poles` specified as a keyword argument, can be used to specify the desired eigenvalues alternatively to or jointly with enforcing a desired stability degree `sdeg` of eigenvalues.  The dimension `nl` of `Al` is the number of freely assignable poles of the solution `X(λ)` and is returned in `info.nl`.  The eigenvalues of `Af-λEf` contain the finite zeros of `G(λ)`, while the zeros  of `Ai-λEi` contain the infinite zeros of `G(λ)`.    The norm of the employed gain `F` is returned in `info.fnorm`. If `G(λ)` has infinite zeros, then the solution `X(λ)` may have infinite poles. The integer vector `info.rdeg` contains the relative row degrees of  `X(λ)` (i.e., the numbers of integrators/delays needed to make each row of `X(λ)` proper).  

If `mindeg = true`, a minimum degree solution is determined as `X(λ) = X0(λ) + Z(λ)XN(λ)`, where `Z(λ)` is determined using order reduction based on a Type 2 minimum dynamic cover. This computation involves using non-orthogonal transformations whose worst condition number is returned in `info.tcond`, in conjunction with  using feedback and feedforward gains, whose norms are returned in `info.fnorm`. High values of these quantities indicate a potential loss of numerical stability of computations. 

If `minreal = true`, the computed realization `sysx` is minimal.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `Ag`, `Bg`, `Cg`, `Dg`, `Af`, `Bf`, `Cf`, `Df`,  the absolute tolerance for the nonzero elements of `Eg` and `Ef`,   and the relative tolerance for the nonzero elements of     `Ag`, `Bg`, `Cg`, `Dg`, `Af`, `Bf`, `Cf`, `Df`, `Eg` and `Ef`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the maximal order of the systems `sysg` and `sysf`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The rank determinations in the performed reductions  are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:*  The dual of method of [1] to solve rational systems is used.

*References:*

[1] A. Varga, "Computation of least order solutions of linear rational equations",  Proc. MTNS'04, Leuven, Belgium, 2004.
