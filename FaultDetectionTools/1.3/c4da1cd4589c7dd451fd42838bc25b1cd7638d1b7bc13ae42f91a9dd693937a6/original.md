```
afdisyn(sysf::FDIModel, SFDI; rdim, nullspace = true, simple = false, minimal = true, separate = false,
                       gamma = 1, epsreg = 0.1, sdegzer, nonstd = 1, freq, sdeg, smarg, poles, 
                       HDesign, HDesign2, scale2, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the *approximate fault detection and isolation problem* (AFDIP) for a given synthesis model `sysf` with additive faults and a given binary structure matrix `SFDI` with `nb` rows (specifications).  The computed stable and proper filter objects `Q` and `R` contain the  fault detection and isolation filter, representing the solution of the AFDIP, and its internal form, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs`, `info.degs2`, `info.HDesign`,  `info.HDesign2` and`info.gap` contains additional synthesis related information (see below). 

The continuous- or discrete-time system `sysf.sys` is in a standard or descriptor state-space form `sysf.sys = (A-λE,B,C,D)`, which corresponds to the input-output form  

```
   y = Gu(λ)*u + Gd(λ)*d + Gf(λ)*f + Gw(λ)*w + Ga(λ)*aux,
```

with the Laplace- or Z-transformed plant outputs `y`, control inputs `u`,  disturbance inputs `d`, fault inputs `f`, noise inputs `w` and auxiliary  inputs `aux`, and with `Gu(λ)`, `Gd(λ)`, `Gf(λ)`, `Gw(λ)`, and `Ga(λ)` the corresponding  transfer-function matrices. The indices of control, disturbance, fault, noise and auxiliary inputs are contained in the associated integer vectors  `sysf.controls`, `sysf.disturbances`, `sysf.faults`, `sysf.noise` and `sysf.aux`, respectively.

The fault detection and isolation filter object `Q`, contains in `Q.sys` the resulting bank of `nb` filters.  The `i`-th filter `Q.sys[i]` is in a standard state-space form and generates `r_i`, the `i`-th component (scalar or vector)  of the overall residual vector `r := [r_1; r_2; ...; r_nb]`.  The corresponding input-output (implementation) form of the `i`-th filter is

```
        r_i = Qyi(λ)*y + Qui(λ)*u   ,
```

where `Qyi(λ)` and `Qui(λ)` are the transfer function matrices from the output and control inputs to the `i`-th residual component.  The indices of output and control inputs are contained in the integer vectors  `Q.outputs` and `Q.controls`, respectively.

The fault detection and isolation filter in internal form object `R`, contains `R.sys`, the resulting bank of `nb`  internal form of the filters.   The `i`-th filter `R.sys[i]` is in a standard state-space form, which generates the residual signal `r_i`, and corresponds to the  input-output form

```
   r_i = Rui(λ)*u + Rdi(λ)*d + Rfi(λ)*f + Rwi(λ)*w + Rai(λ)*aux ,
```

where 

```
   | Rui(λ) Rdi(λ) Rfi(λ) Rwi(λ) Rai(λ) | := |Qyi(λ) Qui(λ)]*| Gu(λ) Gd(λ) Gf(λ) Gw(λ) Ga(λ) |. 
                                                             |   I     0     0     0     0   |
```

The solution of the AFDIP ensures that for the `i`-th filter, `Rui(λ) = 0`, `Rdi(λ) = 0`,  `Rfi(λ)` has its `j`-th column nonzero if the `(i,j)`-th element of `SFDI` is nonzero,  and the H∞-norm of `Rwi(λ)` satisfies `||Rwi(λ)||∞ < γ`, where the bound `γ` is  specified via the keyword argument `gamma`. The indices of the inputs `u`, `d`, `f`, `w` and `aux` of the resulting filter `R.sys` are  contained in the integer vectors `R.controls` (void), `R.disturbances` (void),  `R.faults`, `R.noise` and `R.aux`, respectively.

The transfer function matrices `Qi(λ) := [ Qyi(λ) Qui(λ) ]` and `Ri(λ) := [ Rui(λ) Rdi(λ) Rfi(λ) Rwi(λ) Rai(λ) ]`  of the `i`-th components of the resulting filters `Q.sys` and `R.sys`, respectively, have, in general, the partitioned forms

```
 Qi(λ) = [ Q1i(λ) ] ,   Ri(λ) = [ R1i(λ) ] ,                      (1)
         [ Q2i(λ) ]             [ R2i(λ) ]
```

where the filters `Q1i(λ)` and `R1i(λ)` with `q1i` outputs are the solution of an  AFDP, while the filters `Q2i(λ)` and `R2i(λ)` with q2i outputs are the solution of an   exact fault detection problem formulated for a reduced system obtained   by decoupling the control and disturbance inputs from the residuals (see [4]).   The overall resulting component filters `Q.sys[i]` and `R.sys[i]` have observable state-space  realizations `(AQi,BQi,CQi,DQi)` and `(AQi,BRi,CQi,DRi)`, respectively, and thus   share the observable pairs `(AQi,CQi)`. 

Various user options can be specified via keyword arguments as follows:

If `minimal = true` (default), least order filter synthesis is performed to determine each of the component filters `Q.sys[i]` and `R.sys[i]` for `i = 1, ...,nb`, while  with `minimal = false` full order synthesis is performed.  

If `exact = true`, an exact synthesis (without optimization) is performed, while  with `exact = false` (default), an approximate synthesis is performed.  

If `HDesign = H1`, then `H1` is an `nb`-dimensional array of full row rank or empty design matrices, where `H1[i]` is the design matrix employed for the synthesis   of the components `Q1i(λ)` and `R1i(λ)` in `(1)` of the `i`-th filter  (default: `HDesign = missing`)

If `HDesign2 = H2`, then `H2` is an `nb`-dimensional array of full row rank or empty design matrices,  where `H2[i]` is the design matrix employed for the synthesis  of the components `Q2i(λ)` and `R2i(λ)` in `(1)` of the `i`-th filter   (default: `HDesign2 = missing`)

`rdim = q` specifies the vector `q`, whose `i`-th component `q[i]` specifies  the number of residual outputs for the `i`-th component filters `Q.sys[i]` and `R.sys[i]`.  If `q` is a scalar, then a vector `rdim` with all components equal to `q` is assumed. If `rdim = missing`, the default value of `q[i]` is chosen as `q[i] = q1i + q2i`, where  the default values of `q1i` and `q2i` are chosen taking into account the rank `rwi`  of `Rwi(λ)` in the reduced system (see [2]),  as follows:  if `HDesign = missing`, then   `q1i = min(1,rwi)`, if `minimal = true`, or `q1i = rwi`, if `minimal = false`;  if `HDesign = H1`, then `q1i` is the row dimension of the nonemty design matrix `H1[i]`, or if `H1[i]` is empty, the above choice for `HDesign = missing` is employed; if `HDesign2 = missing`, then   `q2i = 1-min(1,rwi)`, if `minimal = true`, or `q2i` is set to its maximum achievable value,  if `minimal = false` (see [1]);  if `HDesign2 = H2`, then `q2i` is the row dimension of the nonemty design matrix `H2[i]`, or  if `H2[i]` is empty, the above choice for `HDesign2 = missing` is employed.

`FDfreq = freq` specifies a vector of real frequency values or a scalar real frequency value for strong detectability checks (default: `FDfreq = missing`).

If `nullspace = true` (default), a minimal proper nullspace basis is used at the  initial reduction step, if `separate = false`,  or at all synthesis steps, if `separate = true`. If `nullspace = false`, a full-order observer based nullspace basis is used at the  initial reduction step, if `separate = false`, or at all synthesis steps, if `separate = true`. This option can  only be used for a proper system without disturbance inputs. 

If `simple = true`, simple proper nullspace bases are emplyed for synthesis.  If `simple = false` (default), then no simple bases are computed. 

If `separate = false` (default), a two-step synthesis procedure is employed,  where a minimal proper nullspace basis is used at the  initial reduction step.  If `separate = true`, the filter components are separately determined by solving appropriately formulated fault detection problems. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax`  of the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`FDtol = tol1` specifies the threshold `tol1` for fault detectability checks    (default: `tol1 = 0.0001`).

`FDGainTol = tol2` specifies the threshold `tol2` for strong fault detectability checks    (default: `tol2 = 0.01`). 

`scale2 = σ2` specifies the vector of scaling factors `σ2` to be employed for the components  `Q2i(λ)` and `R2i(λ)` in `(1)`, i.e.,  use  `σ2[i]*Q2i(λ)` and `σ2[i]*R2i(λ)` instead of `Q2i(λ)` and `R2i(λ)`.  (default: For `scale2 = missing`, each `σ2[i]` is chosen to ensure the minimum gap provided by `Q1i(λ)`) 

`gamma = γ` specifies the allowed upper bound for the resulting `∥Rwi(λ)∥∞` (default: `γ = 1`).

`epsreg = ϵ` specifies the value of the regularization parameter `ϵ` used in [`afdsyn`](@ref) (default: `ϵ = 0.1`)

`sdegzer = δ` specifies the prescribed stability degree `δ` for zeros shifting    (default: `δ = −0.05` for a continuous-time system `sysf.sys` and     `δ = 0.95` for a discrete-time system `sysf.sys`).

`nonstd = job` specifies the option to handle nonstandard optimization problems in [`afdsyn`](@ref), as follows:

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

The resulting named tuple `info` contains `(tcond, HDesign, HDesign2, freq, gap)`, where:

`info.tcond` is an `nb`-dimensional vector, whose `i`-th component is the maximum of the condition numbers of the employed  non-orthogonal transformation matrices employed for the synthesis of the `i`-th filter component;  a warning is issued if any `info.tcond[i] >= tcmax`;

`info.HDesign = H1` is an `nb`-dimensional vector of design matrices,  whose `i`-th component `H1[i]` is the design matrix to be employed for the synthesis  of the components `Q1i(λ)` and `R1i(λ)` in `(1)` of  the `i`-th fault detection filter.

`info.HDesign2 = H2` is an `nb`-dimensional vector of design matrices,  whose `i`-th component `H2[i]` is the design matrix to be employed for the synthesis  of the components `Q2i(λ)` and `R2i(λ)` in `(1)` of   the `i`-th fault detection filter.

`info.freq` is the frequency value employed to check the full  row rank admissibility condition.

`info.gap` is an `nb`-dimensional vector, whose `i`-th component is the  achieved gap for the synthesis of the `i`-th filter component.

*Method:* The Procedure AFDI from [1] is implemented to solve  the approximate fault detection and isolation problem. For implementation details, see [2].

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.5.

[2] A. Varga, Fault Detection and Isolation Tools (FDITOOLS) User's Guide,                [arXiv:1703.08480](https://arxiv.org/pdf/1703.08480). 
