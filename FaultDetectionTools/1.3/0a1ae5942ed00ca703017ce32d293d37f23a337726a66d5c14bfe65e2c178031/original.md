```
emmsyn(sysf::FDIModel, sysr::FDIFilterIF; nullspace = true, simple = false, minimal = true, regmin = true, normalize = "gain", 
                       sdeg, smarg, poles, freq, HDesign, tcond, offset, 
                       atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDIFilter, R::FDIFilterIF, info)
```

Solve the *exact model-matching problem* (EMMP) for a given synthesis model `sysf::FDIModel` with additive faults  and a given bank of stable reference filters `sysr::FDIFilterIF`.  The computed stable and proper filter objects `Q` and `R` contain the  bank of fault detection filters,  representing the component-wise solution of the EMMP, and  their internal forms, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs`, `info.M`, `info.freq`  and `info.HDesign`, contains additional synthesis related information (see below). 

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

The fault detection and isolation filter internal form object `R`,  contains in its `i`-th component `R.sys[i]`, the resulting  internal form of the filter  in a standard state-space form,  which generates the `i`-th component `ri` of residual signal , and corresponds to the  input-output form

```
   ri = Rui(λ)*u + Rdi(λ)*d + Rfi(λ)*f + Rwi(λ)*w + Rai(λ)*aux ,
```

where 

```
   | Rui(λ) Rdi(λ) Rfi(λ) Rwi(λ) Rai(λ) | = |Qyi(λ) Qui(λ)|*| Gu(λ) Gd(λ) Gf(λ) Gw(λ) Ga(λ) |. 
                                                            |  I     0     0     0     0    |
```

The component-wise solution of the *standard* EMMP is computed if `sysr.noise` and `sysr.aux` are void and ensures that `Rui(λ) = Mi(λ)*Mrui(λ)`, `Rdi(λ) = Mi(λ)*Mrdi(λ)` and `Rfi(λ) = Mi(λ)*Mrfi(λ)`, where `Mi(λ)` is  the transfer function matrix of a stable, diagonal and invertible updating filter returned in the `i`-th component of the vector `info.M`.  This filter is determined to guarantee the stability of the `i`-th components of resulting filters `Q` and `R`.   If `sysr.noise` and `sysr.aux` are not both void, then  the *extended* EMMP is component-wise solved which additionally ensures `Rwi(λ) = Mi(λ)*Mrwi(λ)` and `Rai(λ) = Mi(λ)*Mrai(λ)`.  The indices of the inputs `u`, `d`, `f`, `w` and `aux` of the resulting filter `R.sys` are  contained in the integer vectors `R.controls`, `R.disturbances`, `R.faults`, `R.noise` and `R.aux`, respectively.

Various user options can be specified via keyword arguments as follows:

If `minimal = true` (default), least order filter syntheses are performed, while  with `minimal = false` no least order synthesis are performed.  

If `regmin = true` (default), the regularization (see [1]) is performed for the case when `sysr.controls` and `sysr.disturbances` are void with the selection of a least order left annihilator `Nl(λ)` such that  `Nl(λ)*[Gu(λ) Gd(λ); I 0 ]`.  If `regmin = false`, the regularization is performed by choosing  `Nl(λ)` a minimal left nullspace basis of `G(λ) = [Gu(λ) Gd(λ); I 0 ]`.  

If `HDesign = H` is a vector of full row rank design matrices,  then `H[i]*Nl(λ)` is used  instead `Nl(λ)` for the synthesis of the `i`-th filter (default: `HDesign = missing`).

An initial reduction step is performed using the nullspace-based approach (see [1])  if `sysr.controls`, `sysr.disturbances`, `sysr.noise` and `sysr.aux` are void and `minimal = false`. In this case,   if `nullspace = true` (default), a minimal proper nullspace basis is used at the initial reduction step, while, if `nullspace = false`, a full-order observer based nullspace basis is used at the  initial reduction step. This later option can  only be used for a proper system without disturbance inputs.  The `nullspace` option is ignored if any of `sysr.controls`, `sysr.disturbances`, `sysr.noise` or `sysr.aux` is non-void or if `minimal = true` 

If `simple = true`, a simple proper nullspace basis `Nl(λ)`  is emplyed as left annihilator for synthesis.  The orders of the basis vectors are provided in `info.deg`.  If `simple = false` (default), then a minimal proper nullspace basis is computed. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax`  of the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`freq = val` specifies the value of a test frequency to be employed to  check the full column rank (i.e., left-invertibility) solvability condition  (default: randomly generated in the interval `(0,1)`).  The employed value of `freq` is returned in `info.freq`.

`normalize = job` specifies the option for the normalization   of the diagonal elements of the updating matrices `Mi(λ)` as follows:

```
  job = "gain"    – scale with the gains of the zero-pole-gain representation (default);
  job = "dcgain"  – scale with the DC-gains;
  job = "infnorm" – scale with the values of infinity-norms.
```

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The resulting named tuple `info` contains `(tcond, degs, M, freq, HDesign)`, where:

`info.tcond` is the maximum of the condition numbers of the employed     non-orthogonal transformation matrices; a warning is issued if `info.tcond >= tcmax`;

`info.degs` is an integer vector containing the increasingly ordered degrees of a left minimal    polynomial nullspace basis of `G(λ) := [ Gu(λ) Gd(λ); I 0]` (also the left Kronecker indices of `G(λ)`), if the  state-space realization of `[Gu(λ) Gd(λ)]` is minimal;

`info.M` is a vector of descriptor systems, whose `i`-th system `info.M[i]`  contains the employed stable and invertible updating filter used to solve  the `i`-th EMMP, with a diagonal transfer function matrix `Mi(λ)`; 

`info.freq` is the employed frequency used to check left invertibility  (set to `missing` if no frequency-based left invertibility check was performed)

`info.HDesign` is a vector of design matrices `H`, where `H[i]` is the design matrix  employed for the synthesis of the `i`-th component of the fault detection filter `Q`;  `H[i]` is an empty matrix if no design matrix was involved.

*Method:* The synthesis Procedures EMM and EMMS from [1] are used  to determine the component filters.   Procedure EMM relies on the model-matching synthesis method proposed in    [2], while Procedure EMMS uses the inversion-based method proposed in [3].    Procedure EMM is generally employed, unless a strong exact fault    detection and isolation problem (strong EFDIP) is solved, in   which case Procedure EMMS is used. 

The strong EFDIP corresponds to the choice of each component of the bank of    reference filters `sysr` such that   `Mrui(λ) = 0`, `Mrdi(λ) = 0`, `Mrfi(λ)` is invertible, `Mrwi(λ) = 0` and `Mrai(λ) = 0`.    In this case, only the indices of fault inputs `sysr.faults` must be specified   and the indices of the rest of inputs must be void.    The solution of a fault estimation problem can be targeted by   choosing `Mrfi(λ) = ei`, where `ei` is the `i`-th row of the appropriate identity matrix,  and checking that the resulting `info.M = 1`. 

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.6.

[2] A. Varga, New computational approach for the design of fault       detection and isolation filters.        In M. Voicu (Ed.), "Advances in Automatic Control", vol. 754 of        The Kluwer International Series in Engineering and Computer Science,        Kluwer Academic Publishers, pp. 367-381, 2003.

[3] A. Varga. New computational paradigms in solving fault detection        and isolation problems. Annual Reviews in Control, 37:25–42, 2013. 
