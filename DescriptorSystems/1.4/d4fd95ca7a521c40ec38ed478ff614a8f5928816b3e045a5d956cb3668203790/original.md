```
glmcover2(sys1, sys2; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol) -> (sysx, sysy, info)
```

Determine for the proper descriptor systems `sys1 = (A1-λE1,B1,C1,D1)` and  `sys2 = (A2-λE2,B2,C2,D2)` with the transfer function matrices `X1(λ)` and `X2(λ)`,  respectively, using a left minimum dynamic cover of Type 2 based  order reduction, the descriptor systems `sysx` and `sysy` with the  transfer function matrices `X(λ)` and `Y(λ)`, respectively, such that 

```
X(λ) = X1(λ) + Y(λ)*X2(λ) ,
```

and `sysx` has order less than the order of `sys1`.  

The call with

```
glmcover2(sys, p1; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol) -> (sysx, sysy, info)
```

uses the compound descriptor system `sys = (A-λE,B, [C1; C2],[D1; D2])`,  where `C1` and `D1` have `p1` rows and `E` is invertible, to define   the proper descriptor systems `sys1 = (A-λE,B,C1,D1)` and `sys2 = (A-λE,B,C2,D2)` (i.e., `A1-λE1 = A2-λE2 = A-λE` and `B1 = B2 = B`).   

The resulting descriptor systems `sysx` and `sysy` have observable realizations of the form `sysx = (Ao-λEo,Bo1,Co,Do1)` and `sysy = (Ao-λEo,Bo2,Co,Do2)`,  where the pencil `[Ao-λEo; Co]` is in a (observability) staircase form,   with `νl[i] x νl[i+1]` full row rank diagonal blocks, for `i = 1, ..., nl`,  with `νl[nl+1] := p1`. 

The resulting named triple `info` contains `(stdim, tcond, fnorm, gnorm)`,  where `info.stdim = νl` is a vector which contains the column dimensions of the blocks of the staircase form `[Ao-λEo; Co]`, `info.tcond` is the maximum of  the Frobenius-norm condition numbers of the employed non-orthogonal  transformation matrices, `info.fnorm` is  the Frobenius-norm of the (internally) employed output-injection gain to reduce the order, and  `info.gnorm` is the Frobenius-norm of the (internally) employed output-feedforward gain.  Large values of  `info.tcond`,`info.fnorm` or `info.gnorm` indicate possible loss of  numerical stability of computations. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A1`, `B1`, `C1`, `D1`, `A2`, `B2`, `C2`, `D2`,  the absolute tolerance for the nonzero elements of `E1` and `E2`,   and the relative tolerance for the nonzero elements of  `A1`, `B1`, `C1`, `D1`, `A2`, `B2`, `C2`, `D2`, `E1` and `E2`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the maximal order of the systems `sys1` and `sys2`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`. 

The rank determinations in the performed reductions  are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Note:* `glmcover2` also works for arbitrary descriptor system `sys1`,  if `sys2` is proper. For an improper system `sys1`, the order  reduction is performed only for the proper part of `sys1`, while the  polynomial part of `sys1` is included without modification in the   resulting realization of `sysx`. In this case, `info.stdim = νl` contains the information corresponding to the proper part of `sysx`. 

*Method:* The dual of method  of [1] is used to compute Type 2 minimum dynamic covers  for standard systems and the dual of method of [2] for proper descriptor systems.    The resulting McMillan degree of `sysx` is the least achievable one provided the realization of `sys2` is maximally controllable  (i.e., the pair `(A2+F*C2-λE2,B2+F*D2)` is controllable for any `F`). 

References:

[1] A. Varga, Reliable algorithms for computing minimal dynamic covers,     Proc. CDC'03, Maui, Hawaii, 2003.

[2] A. Varga. Reliable algorithms for computing minimal dynamic covers for      descriptor systems. Proc. MTNS Symposium, Leuven, Belgium, 2004. 
