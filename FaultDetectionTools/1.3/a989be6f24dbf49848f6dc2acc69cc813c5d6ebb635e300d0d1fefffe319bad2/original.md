```
ammsyn(sysf::FDIModel, sysr::FDIFilterIF; nullspace = true, simple = false, mindeg = false, 
                       regmin = true, normalize = "infnorm", H2syn = false, reltol = 1.e-4, 
                       sdeg, smarg, poles, freq, HDesign, tcond, offset, 
                       atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the *approximate model-matching problem* (AMMP) for a given synthesis model `sysf::FDIModel` with additive faults  and a given bank of stable reference filters `sysr::FDIFilterIF`. The computed stable and proper filter objects `Q` and `R` contain the  bank of fault detection filters, representing the component-wise solution of the AMMP, and  their internal forms, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs`, `info.M`, `info.freq`,  `info.HDesign`, `info.nonstandard`, `info.gammaopt0`, `info.gammaopt` and `info.gammasub`,   contains additional synthesis related information (see below). 

The continuous- or discrete-time system `sysf.sys` is in a standard or descriptor state-space form `sysf.sys = (A-λE,B,C,D)`, which corresponds to the input-output form  

```
   y = Gu(λ)*u + Gd(λ)*d + Gf(λ)*f + Gw(λ)*w + Ga(λ)*aux,
```

with the Laplace- or Z-transformed plant outputs `y`, control inputs `u`,  disturbance inputs `d`, fault inputs `f`, noise inputs `w` and auxiliary  inputs `aux`, and with `Gu(λ)`, `Gd(λ)`, `Gf(λ)`, `Gw(λ)`, and `Ga(λ)` the corresponding  transfer-function matrices. The indices of control, disturbance, fault, noise and auxiliary inputs are contained in the associated integer vectors  `sysf.controls`, `sysf.disturbances`, `sysf.faults`, `sysf.noise` and `sysf.aux`, respectively.

The continuous- or discrete-time reference filters packed in `sysr`  are in a standard or descriptor state-space form, where the `i`-th filter  `sysr.sys[i] = (Ari-λEri,Bri,Cri,Dri)` corresponds to the input-output form  

```
   yri = Mrui(λ)*u + Mrdi(λ)*d + Mrfi(λ)*f + Mrwi(λ)*w + Mrai(λ)*aux,
```

with the Laplace- or Z-transformed reference filter outputs `yri`, control inputs `u`,  disturbance inputs `d`, fault inputs `f`, noise inputs `w` and auxiliary  inputs `aux`, and with `Mrui(λ)`, `Mrdi(λ)`, `Mrfi(λ)`, `Mrwi(λ)`, and `Mrai(λ)` the corresponding  transfer-function matrices. The indices of control, disturbance, fault, noise and auxiliary inputs are contained in the associated integer vectors  `sysr.controls`, `sysr.disturbances`, `sysr.faults`, `sysr.noise` and `sysr.aux`, respectively. If any of the above vectors is void, then the corresponding transfer function matrices are considered null. 

The fault detection and isolation filter object `Q`, contains in its `i`-th  component `Q.sys[i]` the resulting filter  in a standard state-space form, which generates the `i`-th component  `ri` of the residual signal.  The corresponding input-output (implementation) form is

```
        ri = Qyi(λ)*y + Qui(λ)*u
```

where `Qyi(λ)` and `Qui(λ)` are the transfer function matrices from the output and control inputs to the residual.  The indices of output and control inputs are contained in the integer vectors  `Q.outputs` and `Q.controls`, respectively.

Let define 

```
  Ge(λ) = | Gu(λ) Gd(λ) Gf(λ) Gw(λ) Ga(λ) |,  Mri(λ) = | Mrui(λ) Mrdi(λ) Mrfi(λ) Mrwi(λ) Mrai(λ) | . 
          |  I     0     0     0     0    |
```

In the standard case, `Ge(λ)` has no zeros on the boundary of the  stability domain, and each resulting component stable filter `Qi(λ) := |Qyi(λ) Qui(λ)|` is  `Qi(λ) = Q0i(λ)`, where `Q0i(λ)` is the optimal solution of the H∞- or H2-norm error minimization problem

```
gammaopt0i = ||Q0i(λ)*Ge(λ)-Mi(λ)*Mri(λ)|| = min,         (1)
```

where `Mi(λ) = M0i(λ)` is an updating factor chosen as follows: `M0i(λ) = I` in the case of emplyoing the  H∞ norm, while in the case of employing the H2 norm, `M0i(λ) = I` for a discrete-time system or, for a continuous-time system,  `M0i(λ)` is determined a stable, diagonal, and invertible transfer function  matrix, which ensures the existence of a finite H2-norm.

In the non-standard case, `Ge(λ)`  has zeros on the boundary of the  stability domain, and each resulting optimal component filter `Q0i(λ)`, which solves  the H∞- or H2-norm error minimization problem (1) is a possibly  unstable or improper. A second updating factor `M1i(λ)` is determined, with    the same properties as `M0i(λ)`, which ensures that the computed stable and   proper filter `Qi(λ) := M1i(λ)*Q0i(λ)` represents a suboptimal solution of an  updated H∞- or H2-norm error minimization problem, for which the    achieved suboptimal model-matching performance is

```
gammasubi = ||Qi(λ)*Ge(λ)-Mi(λ)*Mri(λ)|| ,            (2)
```

where `Mi(λ) := M1i(λ)*M0i(λ)`. The *optimal* solutions `Qti(λ)` of the  updated H∞- or H2-norm error minimization problem 

```
gammaopti = ||Qti(λ)*Ge(λ)-Mi(λ)*Mri(λ)|| = min ,     (3)
```

is still possibly unstable or improper. The values of `gammaopt0i`, `gammaopti` and `gammasubi` are returned in the `i`-th components of the vectors `info.gammaopt0`, `info.gammaopt` and `info.gammasub`, respectively.

The fault detection and isolation filter internal form object `R`,  contains in its `i`-th component `R.sys[i]`, the resulting  internal form of the filter  in a standard state-space form,  which generates the `i`-th component `ri` of residual signal , and corresponds to the  input-output form

```
   ri = Rui(λ)*u + Rdi(λ)*d + Rfi(λ)*f + Rwi(λ)*w + Rai(λ)*aux ,
```

where 

```
   | Rui(λ) Rdi(λ) Rfi(λ) Rwi(λ) Rai(λ) | = Qi(λ)*Ge(λ).
```

The indices of the inputs `u`, `d`, `f`, `w` and `aux` of the resulting filter `R.sys` are  contained in the integer vectors `R.controls`, `R.disturbances`, `R.faults`, `R.noise` and `R.aux`, respectively. The state-space realization of the resulting `Mi(λ)` is returned in the `i`-th component of the vector `info.M`. 

Various user options can be specified via keyword arguments as follows:

If `H2syn = false` (default), a H∞-norm based synthesis is performed, while  if `H2syn = true`, a H2-norm based synthesis is performed. 

`reltol = tol` specifies the relative tolerance `tol` for the desired  accuracy of γ-iteration (default:  `tol = 1.e-4`).

If `mindeg = true`, least order filter syntheses are performed, if possible, while  with `minimal = false` (default) no least order synthesis are performed.  

If `regmin = true` (default), the regularization (see [1]) is performed for the case  when `sysr.controls` and/or `sysr.disturbances` are void with the selection of  a least order left annihilator `Nl(λ)` of `G(λ) = [Gu(λ) Gd(λ); I 0 ]`.  If `regmin = false`, the regularization is performed by choosing a left annihilator `Nl(λ)` as a minimal left nullspace basis of `G(λ)`.  

If `HDesign = H` is a vector of full row rank design matrices,  then `H[i]*Nl(λ)` is used as left annihilator instead `Nl(λ)` for the synthesis of the `i`-th filter (default: `HDesign = missing`).

If `nullspace = true` (default) and `sysr.controls` and/or `sysr.disturbances` are void,  a minimal proper nullspace basis is used at the initial reduction step. If `nullspace = false` and `sysr.controls` and/or `sysr.disturbances` are void,  a full-order observer based nullspace basis is used at the  initial reduction step. This option can  only be used for a proper system without disturbance inputs.  The `nullspace` option is ignored if both `sysr.controls` and `sysr.disturbances` are non-void. 

If `simple = true`, a simple proper nullspace basis   is emplyed as left annihilator for synthesis.  The orders of the basis vectors are provided in `info.deg`.  If `simple = false` (default), then a minimal proper nullspace basis is computed. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax`  of the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`freq = val` specifies the value of a test frequency to be employed to  check the full column rank (i.e., left-invertibility) solvability condition  (default: randomly generated in the interval `(0,1)`).  The employed value of `freq` is returned in `info.freq`.

`normalize = job` specifies the option for the normalization   of the diagonal elements of the updating matrices `Mi(λ)` as follows:

```
  job = "gain"    – scale with the gains of the zero-pole-gain representation;
  job = "dcgain"  – scale with the DC-gains;
  job = "infnorm" – scale with the values of infinity-norms (default).
```

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The resulting named tuple `info` contains `(tcond, degs, M, freq, HDesign, gammaopt0, gammaopt, gammasub, nonstandard)`, where:

`info.tcond` is the maximum of the condition numbers of the employed     non-orthogonal transformation matrices; a warning is issued if `info.tcond >= tcmax`;

`info.degs` is an integer vector containing the increasingly ordered degrees of a left minimal    polynomial nullspace basis of `G(λ) := [ Gu(λ) Gd(λ); I 0]` (also the left Kronecker indices of `G(λ)`), if the  state-space realization of `[Gu(λ) Gd(λ)]` is minimal;

`info.M` is a vector of descriptor systems, whose `i`-th system `info.M[i]`  contains the employed stable and invertible updating filter used to solve  the `i`-th AMMP, with a diagonal transfer function matrix `Mi(λ)`; 

`info.freq` is the employed frequency used to check left invertibility  (set to `missing` if no frequency-based left invertibility check was performed)

`info.HDesign` is a vector of design matrices `H`, where `H[i]` is the design matrix  employed for the synthesis of the `i`-th component of the fault detection filter `Q`;  `H[i]` is an empty matrix if no design matrix was involved.

`info.gammaopt0` is a vector whose `i`-th component is the optimal performance `gammaopt0i` for the `i`-th original problem (1); 

`info.gammaopt` is a vector whose `i`-th component is the optimal performance `gammaopti` for the `i`-th updated problem (3); 

`info.gammasub` is a vector whose `i`-th component is the suboptimal performance `gammasubi` in (2); 

`info.nonstandard` is set to `true` for a non-standard problem     (i.e., `Ge(λ)` has zeros on the boundary of the stability domain), and set to     `false` for a standard problem        (i.e., `Ge(λ)` has no zeros on the boundary of the stability domain). 

*Method:* The synthesis Procedure AMMS from [1] is used  to determine the component filters. The  Procedure AMMS relies on the approximate model-matching synthesis method  proposed in [2]. For more details on computational aspects see [3].  

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.6.

[2] A. Varga, Integrated computational algorithm for solving      H_inf-optimal FDI problems. In Proc. of the IFAC World Congress,      Milano, Italy, pp. 10187–10192, 2011.

[3] A. Varga. Descriptor system techniques in solving H_2/H-Inf-optimal     fault detection and isolation problems". In L. T. Biegler,       S. L. Campbell, and V. Mehrmann (Eds.), Control and Optimization      with Differential-Algebraic Constraints, vol. 23 of Advances in      Design and Control, pp. 105–125. SIAM, 2012. 
