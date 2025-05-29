```
efdsyn(sysf::FDIModel; rdim, nullspace = true, simple = false, minimal = true, 
                       sdeg, smarg, poles, HDesign, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the *exact fault detection problem* (EFDP) for a given synthesis model `sysf` with additive faults. The computed stable and proper filter objects `Q` and `R` contain the  fault detection filter, representing the solution of the EFDP, and its internal form, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs`, `info.S`, and `info.HDesign`,  contains additional synthesis related information (see below). 

The continuous- or discrete-time system `sysf.sys` is in a standard or descriptor state-space form `sysf.sys = (A-λE,B,C,D)`, which corresponds to the input-output form  

```
   y = Gu(λ)*u + Gd(λ)*d + Gf(λ)*f + Gw(λ)*w + Ga(λ)*aux,
```

with the Laplace- or Z-transformed plant outputs `y`, control inputs `u`,  disturbance inputs `d`, fault inputs `f`, noise inputs `w` and auxiliary  inputs `aux`, and with `Gu(λ)`, `Gd(λ)`, `Gf(λ)`, `Gw(λ)`, and `Ga(λ)` the corresponding  transfer-function matrices. The indices of control, disturbance, fault, noise and auxiliary inputs are contained in the associated integer vectors  `sysf.controls`, `sysf.disturbances`, `sysf.faults`, `sysf.noise` and `sysf.aux`, respectively.

The fault detection filter object `Q`, contains in `Q.sys` the resulting filter  in a standard state-space form, which generates the residual signal `r`.  The corresponding input-output (implementation) form is

```
        r = Qy(λ)*y + Qu(λ)*u
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

The solution of the EFDP ensures that `Ru(λ) = 0`, `Rd(λ) = 0`, and `Rf(λ)` has all its columns nonzero.  The indices of the inputs `u`, `d`, `f`, `w` and `aux` of the resulting filter `R.sys` are  contained in the integer vectors `R.controls` (void), `R.disturbances` (void),  `R.faults`, `R.noise` and `R.aux`, respectively.

The resulting filters `Q.sys` and `R.sys` have observable state-space realizations `(AQ,BQ,CQ,DQ)` and `(AQ,BR,CQ,DR)`, respectively, and thus share the observable pairs `(AQ,CQ)`. 

Various user options can be specified via keyword arguments as follows:

If `minimal = true` (default), a least order filter synthesis is performed, while  with `minimal = false` a full order synthesis is performed.  

If `HDesign = H`, a full row rank design matrix `H` is used to build `rdim = q`  linear combinations of the left nullspace basis vectors (default: `HDesign = missing`)

`rdim = q` specifies the desired number `q` of residual outputs for `Q` and `R`.  The default value of `q` is chosen as follows: if `HDesign = missing`, then   `q = 1`, if `minimal = true`, or `q` is the number of the nullspace basis  vectors used for the initial synthesis, if `minimal = false`;  if `HDesign = H` specifies a full row rank design matrix `H`,  then `q` is the row dimension of `H`. 

`FDfreq = freq` specifies a vector of real frequency values or a scalar real frequency value for strong detectability checks (default: `FDfreq = missing`).

If `nullspace = true` (default), a minimal proper nullspace basis is used for the synthesis of the fault detection filter. If `nullspace = false`, a full-order observer based nullspace basis is used.  This option can be only used for a proper system without disturbance inputs. 

If `simple = true`, a simple proper nullspace basis is emplyed for synthesis.  The orders of the basis vectors are provided in `info.deg`.  If `simple = false` (default), then no simple basis is computed. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax`  of the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`FDtol = tol1` specifies the threshold `tol1` for fault detectability checks    (default: `tol1 = 0.0001`).

`FDGainTol = tol2` specifies the threshold `tol2` for strong fault detectability checks    (default: `tol2 = 0.01`). 

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The resulting named tuple `info` contains `(tcond, degs, S, HDesign)`, where:

`info.tcond` is the maximum of the condition numbers of the employed     non-orthogonal transformation matrices; a warning is issued if `info.tcond >= tcmax`;

`info.degs` is an integer vector containing the increasingly ordered degrees of a left minimal    polynomial nullspace basis of `G(λ) := [ Gu(λ) Gd(λ); I 0]` (also the left Kronecker indices of `G(λ)`), if the  state-space realization of `[Gu(λ) Gd(λ)]` is minimal;

`info.S` is the binary structure matrix corresponding to the computed left nullspace basis;

`info.HDesign` is the design matrix `H` employed for the synthesis of     the fault detection filter.

*Method:* The Procedure EFD from [1] is implemented to solve  the exact fault detection problem. For more details on  the least order synthesis of fault detection filters see [2].

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.2.

[2] A. Varga, On computing least order fault detectors using rational nullspace bases.  IFAC SAFEPROCESS'03 Symposium, Washington DC, USA, 2003.
