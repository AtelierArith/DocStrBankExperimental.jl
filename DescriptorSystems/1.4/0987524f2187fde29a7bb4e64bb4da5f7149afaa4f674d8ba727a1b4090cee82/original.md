```
grsol(sysg, sysf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

Determine for the descriptor systems `sysg = (Ag-λEg,Bg,Cg,Dg)` and  `sysf = (Af-λEf,Bf,Cf,Df)` with the transfer function matrices `G(λ)` and `F(λ)`,  respectively, the descriptor system `sysx` with the transfer function matrix `X(λ)`  such that `X(λ)` is the solution of the linear rational equation

```
G(λ)X(λ) = F(λ) .      (1)
```

If `solgen = true`, the descriptor system `sysgen` is determined representing a generator of  all solutions of (1). Its transfer function matrix has the form `GEN(λ) = [ X0(λ) XN(λ) ]`,  such that any `X(λ)` can be generated as

```
X(λ) = X0(λ) + XN(λ)*Z(λ) ,
```

where `X0(λ)` is a particular solution satisfying `G(λ)X0(λ) = F(λ)`,  `XN(λ)` is a proper rational right nullspace basis of `G(λ)` satisfying `G(λ)XN(λ) = 0`, and  `Z(λ)` is an arbitrary rational matrix with suitable dimensions. If `solgen = false`, `sysgen` is set to `nothing`. 

The call with

```
grsol(sysgf, mf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

uses the compound descriptor system `sysgf = (A-λE,[Bg Bf],C,[Dg Df])`,  where `Bf` has `mf` columns, to define   the descriptor systems `sysg = (A-λE,Bg,C,Dg)` and `sysf = (A-λE,Bf,C,Df)` (i.e., `Ag-λEg = Af-λEf = A-λE` and `Cg = Cf = C`). 

The generator `sysgen` has a descriptor system realization `sysgen = (A0-λE0,[B0 BN],C0,[D0 DN])`, which is usually not minimal  (uncontrollable and/or non-dynamic modes present), with  

```
               ( Ar-λEr    *       *    )  
   A0-λE0    = (   0     Af-λEf    *    ) , 
               (   0       0     Ai-λEi ) 

               ( B1 | Br )
   [B0 | BN] = ( B2 | 0  ),  Cg  =   ( Cr   *    *  ) ,
               ( B3 | 0  )
```

with `Er`, `Ef` and `Ai` invertible and upper triangular, `Ei` nillpotent and upper triangular, and `DN` full row rank. The dimensions of the diagonal blocks of `A0-λE0` are  returned in the named tuple `info` as the components `info.nr`, `info.nf`, and `info.ninf`, respectively. 

A minimal order descriptor system realization of the proper basis `XN(λ)` is `(Ar-λEr,Br,Cr,DN)`,  where `Br` and `DN` have `mr` columns (returned in `info.mr`), representing the dimension of the  right nullspace basis. The normal rank `nrank` of  `G(λ)` is returned in `info.nrank`. 

If `mindeg = false`, the solution `sysx` is determined in the form `sysx = (A0+BN*F-λE0,B0,C0+DN*F,D0)`, where the matrix `F = 0`, unless a nonzero stabilizing gain is used such that `Ar+Br*F-λEr` has stable eigenvalues.  The vector `poles` specified as a keyword argument, can be used to specify the desired eigenvalues alternatively to or jointly with enforcing a desired stability degree `sdeg` of eigenvalues.  The dimension `nr` of `Ar` is the number of freely assignable poles of the solution `X(λ)` and is returned in `info.nr`.  The eigenvalues of `Af-λEf` contain the finite zeros of `G(λ)`, while the zeros  of `Ai-λEi` contain the infinite zeros of `G(λ)`.    The norm of the employed gain `F` is returned in `info.fnorm`. If `G(λ)` has infinite zeros, then the solution `X(λ)` may have infinite poles. The integer vector `info.rdeg` contains the relative column degrees of  `X(λ)` (i.e., the numbers of integrators/delays needed to make each column of `X(λ)` proper).  

If `mindeg = true`, a minimum degree solution is determined as `X(λ) = X0(λ) + XN(λ)*Z(λ)`, where `Z(λ)` is determined using order reduction based on a Type 2 minimum dynamic cover. This computation involves using non-orthogonal transformations whose worst condition number is returned in `info.tcond`, in conjunction with  using feedback and feedforward gains, whose norms are returned in `info.fnorm`. High values of these quantities indicate a potential loss of numerical stability of computations. 

If `minreal = true`, the computed realization `sysx` is minimal.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `Ag`, `Bg`, `Cg`, `Dg`, `Af`, `Bf`, `Cf`, `Df`,  the absolute tolerance for the nonzero elements of `Eg` and `Ef`,   and the relative tolerance for the nonzero elements of     `Ag`, `Bg`, `Cg`, `Dg`, `Af`, `Bf`, `Cf`, `Df`, `Eg` and `Ef`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the maximal order of the systems `sysg` and `sysf`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The rank determinations in the performed reductions  are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:*  The method of [1] to solve rational systems is used.

*References:*

[1] A. Varga, "Computation of least order solutions of linear rational equations",  Proc. MTNS'04, Leuven, Belgium, 2004.
