```
ginv(sys; type = "1-2", mindeg = false, fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol, 
          offset = sqrt(ϵ)) -> (sysinv, info)
```

Compute for a descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`  a generalized inverse system `sysinv = (Ai-λEi,Bi,Ci,Di)` with the transfer function matrix `Gi(λ)`  such that two or more of the following *Moore-Penrose conditions* are satisfied:

```
     (1) G(λ)*Gi(λ)*G(λ) = G(λ);        
     (2) Gi(λ)*G(λ)*Gi(λ) = Gi(λ);
     (3) G(λ)*Gi(λ) = (G(λ)*Gi(λ))';
     (4) Gi(λ)*G(λ) = (Gi(λ)*G(λ))'.
```

The desired type of the computed generalized inverse can be specified using the keyword parameter `type` as follows: 

```
  "1-2"     - for a generalized inverse which satisfies conditions (1) and (2) (default);
  "1-2-3"   - for a generalized inverse which satisfies conditions (1), (2) and (3);
  "1-2-4"   - for a generalized inverse which satisfies conditions (1), (2) and (4);
  "1-2-3-4" - for the Moore-Penrose pseudoinverse, which satisfies all conditions (1)-(4).
```

The vector `poles` specified as a keyword argument, can be used to specify the desired eigenvalues alternatively to or jointly with enforcing a desired stability degree `sdeg` of the poles of the  computed generalized inverse. 

The keyword argument `mindeg` can be used to specify the option to determine a minimum order  generalized inverse, if `mindeg = true`, or a particular generalized inverse which has  possibly non-minimal order, if `mindeg = false` (default).

To assess the presence of zeros on the boundary of the stability domain `Cs`, a boundary offset  `β`  can be specified via the keyword parameter `offset = β`.  Accordingly, for a continuous-time setting,  the boundary of `Cs` contains the complex numbers with real parts within the interval `[-β,β]`,  while for a discrete-time setting, the boundary of `Cs` contains the complex numbers with moduli within the interval `[1-β,1+β]`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The returned named tuple `info` has the components `info.nrank`, `info.nfp`, `info.fnorm` and `info.tcond`, where: `info.nrank` is the normal rank of `G(λ)`,  `info.nfp` is the number of freely assignable poles of the inverse `Gi(λ)`,   `info.fnorm` is the maximum of norms of employed feedback gains (also for pole assignment) and  `info.tcond` is the maximum of condition numbers of employed non-orthogonal transformations (see below).  

The rank determinations in the performed reductions  are based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or the more reliable SVD-decompositions, if `fast = false`. The computation of a minimum order inverse is performed by solving suitable minimum dynamic cover problems. These computations involve using non-orthogonal transformations whose maximal condition number is returned in `info.tcond`, in conjunction with  using feedback gains (also for pole assignment), whose maximal norms are returned in `info.fnorm`.  High values of these quantities indicate a potential loss of numerical stability of computations.  

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C` and `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `E`, `B`, `C` and `D`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the maximum dimension of state, input and output vectors of the system `sys`.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 

*Method:*  The methods proposed in [1] are employed in conjunction with  full rank factorizations computed using the approach of [2].

*References:*

[1] A. Varga. Computing generalized inverse systems using matrix pencil methods.     Int. J. of Applied Mathematics and Computer Science, vol. 11, pp. 1055-1068, 2001.

[2] Varga, A. A note on computing range space bases of rational matrices.         arXiv:1707.0048, [https://arxiv.org/abs/1707.00489](https://arxiv.org/abs/1707.00489), 2017.
