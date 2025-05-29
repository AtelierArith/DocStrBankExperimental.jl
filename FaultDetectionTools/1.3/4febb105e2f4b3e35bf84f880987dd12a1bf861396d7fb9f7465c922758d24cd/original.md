```
afdsyn(sysf::FDIModel; rdim, nullspace = true, simple = false, minimal = true, exact = false, 
                       gamma = 1, epsreg = 0.1, sdegzer, nonstd = 1, freq, sdeg, smarg, poles, 
                       HDesign, HDesign2, scale2, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true) 
                          -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the approximate fault detection problem (AFDP) for a given synthesis model `sysf` with additive faults. The computed stable and proper filter objects `Q` and `R` contain the  fault detection filter, representing the solution of the AFDP, and its internal form, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs`, `info.degs2`,  `info.S`, `info.S2`, `info.HDesign`, `info.HDesign2`, `info.freq` and `info.gap` contains additional synthesis related information (see below). 

The continuous- or discrete-time system `sysf.sys` is in a standard or descriptor state-space form `sysf.sys = (A-λE,B,C,D)`, which corresponds to the input-output form  

```
   y = Gu(λ)*u + Gd(λ)*d + Gf(λ)*f + Gw(λ)*w + Ga(λ)*aux,
```

with the Laplace- or Z-transformed plant outputs `y`, control inputs `u`,  disturbance inputs `d`, fault inputs `f`, noise inputs `w` and auxiliary  inputs `aux`, and with `Gu(λ)`, `Gd(λ)`, `Gf(λ)`, `Gw(λ)`, and `Ga(λ)` the corresponding  transfer-function matrices. The indices of control, disturbance, fault, noise and auxiliary inputs are contained in the associated integer vectors  `sysf.controls`, `sysf.disturbances`, `sysf.faults`, `sysf.noise` and `sysf.aux`, respectively.

The fault detection filter object `Q`, contains in `Q.sys` the resulting filter  in a standard state-space form, which generates the residual signal `r`.  The corresponding input-output (implementation) form is

```
        r = Qy(λ)*y + Qu(λ)*u  ,
```

where `Qy(λ)` and `Qu(λ)` are the transfer function matrices from the output and control inputs to the residual.  The indices of output and control inputs are contained in the integer vectors  `Q.outputs` and `Q.controls`, respectively.

The fault detection filter in internal form object `R`, contains `R.sys`, the resulting  internal form of the filter  in a standard state-space form, which generates the residual signal `r`, and corresponds to the  input-output form

```
   r = Ru(λ)*u + Rd(λ)*d + Rf(λ)*f + Rw(λ)*w + Ra(λ)*aux ,
```

where 

```
   | Ru(λ) Rd(λ) Rf(λ) Rw(λ) Ra(λ) | = |Qy(λ) Qu(λ)|*| Gu(λ) Gd(λ) Gf(λ) Gw(λ) Ga(λ) |. 
                                                     |  I     0     0     0     0    |
```

The solution of the AFDP ensures that `Ru(λ) = 0`, `Rd(λ) = 0`, `Rf(λ)` has all its columns nonzero and the H∞-norm of `Rw(λ)` satisfies `||Rw(λ)||∞ < γ`, where the bound `γ` is  specified via the keyword argument `gamma`. The indices of the inputs `u`, `d`, `f`, `w` and `aux` of the resulting filter `R.sys` are  contained in the integer vectors `R.controls` (void), `R.disturbances` (void),  `R.faults`, `R.noise` and `R.aux`, respectively.

The transfer function matrices `Q(λ) = [ Qy(λ) Qu(λ) ]` and `R(λ) = [ Ru(λ) Rd(λ) Rf(λ) Rw(λ) Ra(λ) ]`  of the resulting filters `Q.sys` and `R.sys`, respectively, have, in general, the partitioned forms

```
 Q(λ) = [ Q1(λ) ] ,   R(λ) = [ R1(λ) ] ,                      (1)
        [ Q2(λ) ]            [ R2(λ) ]
```

where the filters `Q1(λ)` and `R1(λ)` with `q1` outputs are the solution of an  AFDP, while the filters `Q2(λ)` and `R2(λ)` with q2 outputs are the solution of an   exact fault detection problem formulated for a reduced system obtained   by decoupling the control and disturbance inputs from the residuals (see [4]).   The overall resulting filters `Q.sys` and `R.sys` have observable state-space  realizations `(AQ,BQ,CQ,DQ)` and `(AQ,BR,CQ,DR)`, respectively, and thus   share the observable pairs `(AQ,CQ)`. 

Various user options can be specified via keyword arguments as follows:

If `minimal = true` (default), a least order filter synthesis is performed, while  with `minimal = false` a full order synthesis is performed.  

If `exact = true`, an exact synthesis (without optimization) is performed, while  with `exact = false` (default), an approximate synthesis is performed.  

If `HDesign = H1`, a design matrix `H1` of full row rank `q1` is used to build `q1`  linear combinations of the left nullspace basis vectors of  `G1(λ) := [ Gu(λ) Gd(λ); I 0]`. `H1` is used in the synthesis of the components  `Q1(λ)` and `R1(λ)` in `(1)` (default: `HDesign = missing`).

If `HDesign2 = H2`, a design matrix `H2` of full row rank `q2` is used to build `q2`  linear combinations of the left nullspace basis vectors of  `G2(λ) := [ Gu(λ) Gd(λ) Gw(λ); I 0 0]`. `H2` is used in the synthesis of the components  `Q2(λ)` and `R2(λ)` in `(1)` (default: `HDesign2 = missing`)

`rdim = q` specifies the desired number `q` of residual outputs for `Q` and `R`.  If `rdim = missing`, the default value of `q` is chosen as `q = q1 + q2`, where  the default values of `q1` and `q2` are chosen taking into account the rank `rw`  of `Rw(λ)` in the reduced system (see [4]), as follows:  if `HDesign = missing`, then   `q1 = min(1,rw)`, if `minimal = true`, or `q1 = rw`, if `minimal = false`;  if `HDesign = H`, then `q1` is the row dimension of the design matrix `H2`. if `HDesign2 = missing`, then   `q2 = 1-min(1,rw)`, if `minimal = true`, or `q2 = nvec-rw`, if `minimal = false`, where `nvec` is the number of the nullspace basis  vectors used for the initial synthesis (see [1]);  if `HDesign2 = H2`, then `q2` is the row dimension of the design matrix `H2`.

`FDfreq = freq` specifies a vector of real frequency values or a scalar real frequency value for strong detectability checks (default: `FDfreq = missing`).

If `nullspace = true` (default), a minimal proper nullspace basis is used for  the initial synthesis of the fault detection filter.  If `nullspace = false`, a full-order observer based nullspace basis is used.  This option can be only used for a proper system without disturbance inputs. 

If `simple = true`, a simple proper nullspace basis is emplyed for synthesis.  The orders of the basis vectors employed for the synthesis are provided in `info.deg` and `info.deg2` (see below).  If `simple = false` (default), then no simple basis is computed. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`scale2 = σ2` specifies the scaling factor `σ2` to be employed for the components  `Q2(λ)` and `R2(λ)` in `(1)`, i.e.,  use  `σ2*Q2(λ)` and `σ2*R2(λ)` instead of `Q2(λ)` and `R2(λ)`.  (default: `σ2` is chosen to ensure the minimum gap provided by `Q1(λ)`) 

`freq = val` specifies the values of a test frequency to be employed to check the  full row rank admissibility condition (default: randomly generated in the interval `(0,1)`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax` of  the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`FDtol = tol1` specifies the threshold `tol1` for fault detectability checks    (default: `tol1 = 0.0001`).

`FDGainTol = tol2` specifies the threshold `tol2` for strong fault detectability checks    (default: `tol2 = 0.01`). 

`gamma = γ` specifies the allowed upper bound for `∥Rw(λ)∥∞` (default: `γ = 1`).

`epsreg = ϵ` specifies the value of the regularization parameter `ϵ` (default: `ϵ = 0.1`)

`sdegzer = δ` specifies the prescribed stability degree `δ` for zeros shifting    (default: `δ = −0.05` for a continuous-time system `sysf.sys` and     `δ = 0.95` for a discrete-time system `sysf.sys`).

`nonstd = job` specifies the option to handle nonstandard optimization problems, as follows:

```
  job = 1 – use the quasi-co-outer–co-inner factorization (default);
  job = 2 – use the modified co-outer–co-inner factorization with the
            regularization parameter `ϵ`;
  job = 3 – use the Wiener-Hopf type co-outer–co-inner factorization;
  job = 4 – use the Wiener-Hopf type co-outer-co-inner factorization with
            zero shifting of the non-minimum phase factor using the
            stabilization parameter `δ`;
  job = 5 – use the Wiener-Hopf type co-outer-co-inner factorization with
            the regularization of the non-minimum phase factor using the
            regularization parameter `ϵ`.
```

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The resulting named tuple `info` contains `(tcond, degs, degs2, S, S2, HDesign, HDesign2, freq, gap)`, where:

`info.tcond` is the maximum of the condition numbers of the employed     non-orthogonal transformation matrices; a warning is issued if `info.tcond >= tcmax`;

`info.degs` is an integer vector containing the increasingly ordered degrees of a left minimal    polynomial nullspace basis of `G1(λ) := [ Gu(λ) Gd(λ); I 0]` (also the left Kronecker indices of `G1(λ)`), if the  state-space realization of `[Gu(λ) Gd(λ)]` is minimal.  This information has been used in the case  `minimal = true` to determine the least order of components `Q1(λ)` and `R1(λ)` in `(1)`.

`info.degs2` is an integer vector containing the increasingly ordered degrees of a left minimal    polynomial nullspace basis of `G2(λ) := [ Gu(λ) Gd(λ) Gw(λ); I 0 0]` (also the left Kronecker indices of `G2(λ)`), if the  state-space realization of `[Gu(λ) Gd(λ) Gw(λ)]` is minimal.  This information has been used in the case  `minimal = true` to determine the least order of components `Q2(λ)` and `R2(λ)` in `(1)`.

`info.S` is the binary structure matrix of the reduced system  corresponding to the computed left nullspace basis of `G1(λ) := [ Gu(λ) Gd(λ); I 0]`;

`info.S2` is the binary structure matrix of the reduced system  corresponding to the computed left nullspace basis of `G2(λ) := [ Gu(λ) Gd(λ)  Gw(λ); I 0 0]`;

`info.HDesign` is the design matrix `H1` employed for the synthesis of     the components `Q1(λ)` and `R1(λ)` in `(1)` of the fault detection filter;

`info.HDesign2` is the design matrix `H2` employed for the synthesis of  the components `Q2(λ)` and `R2(λ)` in `(1)` of the fault detection filter;

`info.freq` is the frequency value employed to check the full  row rank admissibility condition;

`info.gap` is the achieved gap `∥Rf(λ)∥∞−/∥Rw(λ)∥∞`, where the H−minus index is computed over the whole frequency range, if `FDfreq = missing`, or over the frequency values contained in `freq` if `FDfreq = freq`.

*Method:* An extension of the Procedure AFD from [1] is implemented to solve  the approximate fault detection problem (see also [2] and Remark 5.10 of [1]).  The employed regularization approach, based on the modified co-outer-co-inner  factorization, is discussed in [3], see also Remark 5.8 of [1].  For the details of the implemented method, see the documentation of the *afdsyn* function in [4]. 

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.3.

[2] A. Varga, General computational approach for optimal fault detection.                Proc. IFAC Symposium SAFEPROCESS, Barcelona, Spain, pp. 107–112, 2009.

[3] K. Glover and A. Varga, On solving non-standard H-/H_2/inf fault detection problems.                Proc. IEEE CDC, Orlando, FL, USA, pp. 891–896, 2011.

[4] A. Varga, Fault Detection and Isolation Tools (FDITOOLS) User's Guide,                [arXiv:1703.08480](https://arxiv.org/pdf/1703.08480). 
