```
efdisyn(sysf::FDIModel, SFDI; rdim, nullspace = true, simple = false, minimal = true, separate = false,
                       sdeg, smarg, poles, HDesign, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the *exact fault detection and isolation problem* (EFDIP) for a given synthesis model `sysf` with additive faults and a given binary structure matrix `SFDI` with `nb` rows (specifications).  The computed stable and proper filter objects `Q` and `R` contain the  fault detection and isolation filter, representing the solution of the EFDIP, and its internal form, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs` and `info.HDesign`,  contains additional synthesis related information (see below). 

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

The solution of the EFDIP ensures that for the `i`-th filter, `Rui(λ) = 0`, `Rdi(λ) = 0`, and  `Rfi(λ)` has its `j`-th column nonzero if the `(i,j)`-th element of `SFDI` is nonzero.  The indices of the inputs `u`, `d`, `f`, `w` and `aux` of the resulting filter `R.sys` are  contained in the integer vectors `R.controls` (void), `R.disturbances` (void),  `R.faults`, `R.noise` and `R.aux`, respectively.

The resulting component filters `Q.sys[i]` and `R.sys[i]` have observable state-space realizations `(AQi,BQi,CQi,DQi)` and `(AQi,BRi,CQi,DRi)`, respectively, and thus share the observable pairs `(AQi,CQi)`. 

Various user options can be specified via keyword arguments as follows:

If `minimal = true` (default), least order filter synthesis is performed to determine each of the component filters `Q.sys[i]` and `R.sys[i]` for `i = 1, ...,nb`, while  with `minimal = false` full order synthesis is performed.  

If `HDesign = H`, then `H` is an `nb`-dimensional array of full row rank or empty design matrices `H = [H_1, ..., H_nb]`, where `H_i` is the design matrix employed for the synthesis of the `i`-th component filter (default: `HDesign = missing`)

`rdim = q` specifies the vector `q`, whose `i`-th component `q[i]` specifies  the number of residual outputs for the `i`-th component filters `Q.sys[i]` and `R.sys[i]`.  If `q` is a scalar, then a vector `rdim` with all components equal to `q` is assumed. The default value of `q[i]` is chosen as follows: if `HDesign = missing` or `H_i` is empty then   `q[i] = 1`, if `minimal = true`, or `q[i]` is the number of the nullspace basis  vectors used for the synthesis of `Q.sys[i]` and `R.sys[i]`, if `minimal = false`;  if  `H_i` specifies a full row rank design matrix, then `q[i]` is the row dimension of `H_i`. 

`FDfreq = freq` specifies a vector of real frequency values or a scalar real frequency value for strong detectability checks (default: `FDfreq = missing`).

If `nullspace = true` (default), a minimal proper nullspace basis is used at the  initial reduction step, if `separate = false`,  or at all synthesis steps, if `separate = true`. If `nullspace = false`, a full-order observer based nullspace basis is used at the  initial reduction step, if `separate = false`, or at all synthesis steps, if `separate = true`. This option can  only be used for a proper system without disturbance inputs. 

If `simple = true`, simple proper nullspace bases are emplyed for synthesis.  The orders of the basis vectors employed for the synthesis of `i`-th filter are provided in `info.deg[i]`.  If `simple = false` (default), then no simple bases are computed. 

If `separate = false` (default), a two-step synthesis procedure is employed,  where a minimal proper nullspace basis is used at the  initial reduction step.  If `separate = true`, the filter components are separately determined by solving appropriately formulated fault detection problems. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax`  of the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`FDtol = tol1` specifies the threshold `tol1` for fault detectability checks    (default: `tol1 = 0.0001`).

`FDGainTol = tol2` specifies the threshold `tol2` for strong fault detectability checks    (default: `tol2 = 0.01`). 

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The resulting named tuple `info` contains `(tcond, degs, HDesign)`, where:

`info.tcond` is an `nb`-dimensional vector, whose `i`-th component is the maximum of the condition numbers of the employed  non-orthogonal transformation matrices employed for the synthesis of the `i`-th filter component;  a warning is issued if any `info.tcond[i] >= tcmax`;

`info.degs` is an `nb`-dimensional vector, whose `i`-th component is an integer vector  containing the degrees of the basis vectors of the employed simple nullspace basis for the synthesis of the `i`-th filter component, if `simple = true,  and the degrees of the basis vectors of an equivalent polynomial nullspace basis, if`simple = false`;

`info.HDesign` is an `nb`-dimensional vector, whose `i`-th component  is the design matrix `H_i` employed for the synthesis of  the `i`-th fault detection filter.

*Method:* The Procedure EFDI from [1] is implemented to solve  the exact fault detection and isolation problem.  This procedure relies on the nullspace-based synthesis method proposed in [2]. For more  details on the least order synthesis of fault detection filters see [3].

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.4.

[2] A. Varga,  On designing least order residual generators for fault detection      and isolation. 16th International Conference on Control Systems and       Computer Science, Bucharest, Romania, 2007.

[3] A. Varga, On computing least order fault detectors using rational nullspace bases.      IFAC SAFEPROCESS'03 Symposium, Washington DC, USA, 2003.
