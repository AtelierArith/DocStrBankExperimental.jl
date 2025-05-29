```
grnull(sys; polynomial = false, simple = false, inner = false, fast = true, poles = missing, sdeg = missing,  
       atol = 0, atol1 = atol, atol2 = atol, rtol, offset = sqrt(ϵ) ) -> (sysrnull, info)
```

Determine for the descriptor systems `sys = (A-λE,B,C,D)` with the `p x m` transfer function matrix `G(λ)`,  the descriptor system `sysrnull = (Ar-λEr,Br,Cr,Dr)` with the transfer function matrix `Nr(λ)`  such that `Nr(λ)` is a minimal rational right nullspace basis of `G(λ)` and satisfies `G(λ)*Nr(λ) = 0`.     

For the call with

```
grnull(sys, p2; polynomial = false, simple = false, inner = false, fast = true, poles = missing, sdeg = missing,  
       atol = 0, atol1 = atol, atol2 = atol, rtol, offset = sqrt(ϵ) ) -> (sysrnull, info)
```

`sys` contains the compound system `sys = [sys1; sys2]`, with `G(λ)`, the transfer function matrix of `sys1`, and  `G2(λ)`, the transfer function matrix of `sys2`, and has the descriptor realization `sys = (A-λE,B,[C;C2],[D;D2])`,  where `sys2` has `p2` outputs. The resulting `sysrnull` contains the compound system  `[sysrnull1; sys2*sysrnull1] = (Ar-λEr,Br,[Cr;Cr2],[Dr;Dr2])`, where `sysrnull1 = (Ar-λEr,Br,Cr,Dr)` has the transfer function matrix `Nr(λ)`, which is a rational right nullspace basis of `G(λ)` satisfying `G(λ)*Nr(λ) = 0` and `sys2*sysrnull1 = (Ar-λEr,Br,Cr2,Dr2)` has the transfer function matrix `G2(λ)*Nr(λ)`. 

The returned named tuple `info` has the components `info.nrank`, `info.stdim`, `info.degs`, `info.fnorm` and `info.tcond`.

If `polynomial = false`, the resulting `sysrnull` has a proper transfer function matrix,  while for `polynomial = true` the resulting `sysrnull` has a polynomial transfer function matrix.  The resulting basis `Nr(λ)` contains `m-r` basis vectors, where `r = rank G(λ)`. The rank `r` is returned in `info.nrank`. If `simple = true`, the resulting basis is *simple* and satisfies the condition that the sum of the  number of poles of the `m-r` basis vectors is equal to the number of poles of `Nr(λ)` (i.e., its McMillan degree) . 

For a non-simple proper basis, the realization `(Ar-λEr,Br,Cr,Dr)` is controllable and the pencil `[Br Ar-λEr]` is in a controllable staircase form. The column dimensions of the full row rank diagonal blocks are returned in `info.stdim` and the corresponding right Kronecker indices are returned in `info.degs`.   For a simple basis, the regular pencil `Ar-λEr` is block diagonal, with the `i`-th block of size `info.deg[i]`  (the `i`-th right Kronecker index) for a proper basis and  `info.deg[i]+1` for a polynomial basis.  The dimensions of the diagonal blocks are returned in this case in `info.stdim`, while the increasing numbers of poles of  the basis vectors are returned in `info.degs`. For the `i`-th basis vector `vi(λ)` (i.e., the `i`-th column of `Nr(λ)`)  a minimal realization can be explicitly constructed as `(Ari-λEri,Bri,Cr,Dr[:,i])`, where `Ari`, `Eri` and `Bri` are the `i`-th diagonal blocks of `Ar`, `Er`, and `Br`, respectively, and `Dr[:,i]` is the `i`-th column of `Dr`.  The corresponding realization of `G2(λ)*vi(λ)` can be constructed as `(Ari-λEri,Bri,Cr2,Dr2[:,i])`, where `Dr2[:,i]` is the `i`-th column of `Dr2`.

For a proper basis, the poles of `Nr(λ)` can be freely assigned, by assigning the  eigenvalues of the pencil `Ar-λEr`. The vector `poles`, specified as a keyword argument, can be used to specify the desired eigenvalues, alternatively to or jointly with enforcing a desired stability degree `sdeg` of the real parts of the eigenvalues,  for a continuous-time system, or the moduli of eigenvalues, for a discrete-time system.  If `inner = true`, the resulting basis `Nr(λ)` is *inner*, i.e., `Nr(λ)'*Nr(λ) = I`, where `Nr(s)' = transpose(Nr(-s))` for a  continuous-time system with `λ = s` and `Nr(z)' = transpose(Nr(1/z))` for a discrete-time system with `λ = z`.  If the proper basis is simple, each of the resulting individual basis vector is inner.  If `sys2` has poles on the boundary of the appropriate stability domain `Cs`, which are not poles of `sys1` too,  then there exists no inner `Nr(λ)` such that `G2(λ)*Nr(λ)` is stable. An offset can be specified via the keyword parameter `offset = β` to be used to assess the existence of zeros on the stability domain boundary. Accordingly, for a continuous-time system,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time system, the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 

The rank determinations in the performed reductions  are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`. The computation of simple bases involves the solution of several Type 1 minimum dynamic cover problems. This computation involves using non-orthogonal transformations whose worst condition number is returned in `info.tcond`, in conjunction with  using feedback gains, whose norms are returned in `info.fnorm`. High values of these quantities indicate a potential loss of numerical stability of computations.  

*Note:* The resulting realization of `sysrnull` is minimal provided the realization of `sys` is minimal.  However, `sysrnull1` is a minimal basis only if the realization (A-lambda E,B,C,D) of `sys1` is  minimal. In this case, `info.degs` are the degrees of the vectors of a minimal polynomial basis or,  if `simple = true`, of the resulting minimal simple proper basis. 

*Method:* The computation of a minimal proper right nullspace basis is based on [1]; see also [2]. For the computation of a minimal simple proper  right nullspace basis the method of [3] is emloyed to compute a simple basis from a minimal proper basis. For the computation of an inner proper right nullspace basis, the inner factor of an inner-outer factorization of `Nr(λ)` is explicitly  constructed using formulas given in [4]. 

*References:*

[1] T.G.J. Beelen.     New algorithms for computing the Kronecker structure of a pencil      with applications to systems and control theory.      Ph. D. Thesis, Technical University Eindhoven, 1987.

[2] A. Varga.     On computing least order fault detectors using rational nullspace bases.      IFAC SAFEPROCESS'03 Symposium, Washington DC, USA, 2003.

[3] A. Varga.     On computing nullspace bases – a fault detection perspective.      Proc. IFAC 2008 World Congress, Seoul, Korea, pages 6295–6300, 2008.

[4] K. Zhou, J. C. Doyle, and K. Glover.      Robust and Optimal Control. Prentice Hall, 1996.
