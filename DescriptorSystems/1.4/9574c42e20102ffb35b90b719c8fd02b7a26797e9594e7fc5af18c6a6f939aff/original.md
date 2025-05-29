```
grange(sys; zeros = "none", atol = 0, atol1 = atol, atol2 = atol, rtol, 
       fast = true, offset = sqrt(ϵ)) -> (sysr, sysx, info)
```

Compute for the descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`,  the proper descriptor system `sysr = (Ar-λEr,Br,Cr,Dr)` with a full column rank  transfer function matrix `R(λ)` such that `Range(G(λ)) = Range(R(λ))` and the   descriptor system `sysx = (A-λE,B,Cx,Dx)` with the full row rank transfer function matrix `X(λ)`, which satisfies

```
 G(λ) = R(λ)*X(λ) ,
```

representing a full rank factorization of `G(λ)`.   The number of columns of `R(λ)` is the normal rank `r` of `G(λ)`.  The columns of `R(λ)` form a rational basis of the range (or image) space of the rational matrix `G(λ)`.  A selected set of zeros of `G(λ)` are included as zeros of `R(λ)`. 

The resulting named triple `info` contains `(nrank, nfuz, niuz)`, where `info.nrank = r`,  the normal rank of `G(λ)`, `info.nfuz` is the number of finite zeros of `sys` on  the boundary of the stability domain `Cs`, and `info.niuz` is the number of infinite zeros of `sys` in  the continuous-time case and is set to `0` in the discrete-time case. 

Depending on the value of the keyword parameter `zeros`, the following options can be selected  for the zeros of `G(λ)` to be included in `R(λ)`:

```
 "none"       - include no zeros (default) 
 "all"        - include all zeros of `sys`
 "unstable"   - include all unstable zeros of `sys`
 "s-unstable" - include all strictly unstable zeros of `sys`, both finite and infinite
 "stable"     - include all stable zeros of `sys`
 "finite"     - include all finite zeros of `sys`
 "infinite"   - include all infinite zeros of `sys`
```

If `inner = true`, the resulting basis `R(λ)` is *inner*, i.e., `R(λ)'*R(λ) = I`, where `R(s)' = transpose(R(-s))` for a  continuous-time system with `λ = s` and `R(z)' = transpose(R(1/z))` for a discrete-time system with `λ = z`.  This option can be used only in conjunction with `zeros = "none"` or `zeros = "unstable"`. 

For a continuous-time system `sys`, the stability domain `Cs` is defined as the set of  complex numbers with real parts at most `-β`,  while for a discrete-time system `sys`, `Cs` is the set of complex numbers with  moduli at most `1-β` (i.e., the interior of a disc of radius `1-β` centered in the origin).  The boundary offset  `β` to be used to assess the stability of zeros and their number  on the boundary of `Cs` can be specified via the keyword parameter `offset = β`. Accordingly, for a continuous-time system,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time system, the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C` and `D`, the absolute tolerance for the nonzero elements of `E`,    and the relative tolerance for the nonzero elements of `A`, `E`, `B`, `C` and `D`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol`. 

For the assessment of zeros, the system pencil `[A-λE B; C D]` is reduced to a  special Kronecker-like form (see [2]). In this reduction, the  performed rank decisions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

*Method:*  The range computation method is described in [1] and is based on  the reduction algorithm of [2], which has been adapted to deal with  several zero selection options. The computation of the involved  Kronecker-like form is based on the algorithm of [3].

*References:*

[1] Varga, A.     A note on computing the range of rational matrices.      arXiv:1707.0048, [https://arxiv.org/abs/1707.0048](https://arxiv.org/abs/1707.004), 2017.

[2] C. Oara.     Constructive solutions to spectral and inner–outer factorizations      respect to the disk. Automatica,  41, pp. 1855–1866, 2005. 

[3] C. Oara and P. Van Dooren.      An improved algorithm for the computation of structural invariants of a system pencil and related geometric aspects.      Syst. Control Lett., 30:39–48, 1997.
