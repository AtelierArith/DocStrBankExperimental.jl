```
emdsyn(sysm::MDMModel; rdim, MDSelect, nullspace = true, simple = false, minimal = true, 
                       emtest = false, normalize = false, fast = true, 
                       sdeg, smarg, poles, HDesign, MDtol, MDGainTol, MDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol) 
                       -> (Q::MDFilter, R::MDFilterIF, info)
```

Solve the *exact model detection problem* (EMDP) for a given multiple synthesis model `sysm::MDMModel`. The computed stable and proper filter objects `Q` and `R` contain the  model detection filter, representing the solution of the EMDP, and its internal form, respectively.

The returned named tuple `info`, with the components `info.tcond`, `info.degs`, `info.MDperf`, and `info.HDesign`,  contains additional synthesis related information (see below). 

For a multiple synthesis model `sysm` containing `N` stable component models,  the `i`-th component system `sysm.sys[i]` has a descriptor realization of the form  `sysm.sys[i] = (Ai-λEi,Bi,Ci,Di)` and the corresponding input-output form is

```
  yi = Gui(λ)*u + Gdi(λ)*di + Gwi(λ)*wi + Gvi(λ)*vi
```

with the Laplace- or Z-transformed plant outputs `yi`, control inputs `u`,  disturbance inputs `di`, noise inputs `wi`, and auxiliary inputs `vi`,   and with `Gui(λ)`, `Gdi(λ)`, `Gwi(λ)` and  `Gvi(λ)`, the corresponding transfer function matrices. 

The model detection filter object `Q`, contains in `Q.sys` the resulting bank of `N` filters.  The `i`-th filter `Q.sys[i]` is in a standard state-space form and generates `r_i`,  the `i`-th component (scalar or vector) of the overall residual vector `r := [r_1; r_2; ...; r_N]`.  The corresponding input-output (implementation) form of the `i`-th filter is

```
        r_i = Qyi(λ)*y + Qui(λ)*u   ,
```

where `Qyi(λ)` and `Qui(λ)` are the transfer function matrices from the output and control inputs to the `i`-th residual component.  The dimensions of output and control inputs are contained in the integers   `Q.ny` and `Q.mu`, respectively.

The model detection filter internal form object `R`, contains `R.sys`, the resulting array of `N × N`  internal form of the filters.   The `(i,j)`-th component filter `R.sys[i,j]` is in a standard state-space form,  generates the residual signal `r_ij`, and corresponds to the  input-output form

```
   r_ij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,
```

where 

```
   | Ruij(λ) Rdij(λ) Rwij(λ) Raij(λ) | := |Qyi(λ) Qui(λ)]*| Guj(λ) Gdj(λ) Gwj(λ) Gaj(λ) |. 
                                                          |   I    0      0      0      |
```

The solution of the EMDP ensures that for the `i`-th filter, `Ruii(λ) = 0`, `Rdii(λ) = 0`, and  `[Ruij(λ) Rdij(λ)]` $\neq$ `0` for `j` $\neq$ `i`.

Various user options can be specified via keyword arguments as follows:

`MDSelect = ifilt` specifies in the vector `ifilt` the indices of the desired filters to be designed (default: `ifilt = 1:N`)

If `minimal = true` (default), least order filter synthesis is performed to determine  each of the component filters `Q.sys[i]` for `i = 1, ...,N` and `R.sys[i,j]` for `i, j = 1, ...,N`  while  with `minimal = false` full order synthesis is performed.  

If `HDesign = H`, then `H` is an `N`-dimensional array of full row rank or empty design matrices `H = [H_1, ..., H_N]`, where `H_i` is the design matrix employed for the synthesis of the `i`-th component filter (default: `HDesign = missing`)

`rdim = q` specifies the vector `q`, whose `i`-th component `q[i]` specifies  the number of residual outputs for the `i`-th component filter `Q.sys[i]`.  If `q` is a scalar, then a vector `rdim` with all components equal to `q` is assumed. The default value of `q[i]` is chosen as follows: if `HDesign = missing` or `H_i` is empty then   `q[i] = 1`, if `minimal = true`, or `q[i]` is the number of the nullspace basis  vectors used for the synthesis of `Q.sys [i]`, if `minimal = false`;  if  `H_i` specifies a full row rank design matrix, then `q[i]` is the row dimension of `H_i`. 

If `emdtest = false` (default), only the input channels are used for model detectability tests. If `emdtest = true`, extended model detectability tests are performed using both control and disturbance input channels.  

`MDfreq = ω` specifies a vector of real frequency values or a scalar real frequency value for strong model detectability checks (default: `MDfreq = missing`).

If `nullspace = false` (default),  a full-order observer based nullspace basis is  used for the synthesis of the `i`-th filter whenever the `i`-th component system has no disturbance inputs. Otherwise, minimal proper nullspace bases are used.  If `nullspace = true`, minimal proper nullspace bases are used for the synthesis of the model detection filters. 

If `simple = true`, simple proper nullspace bases are emplyed for synthesis.  The orders of the basis vectors employed for the synthesis of the `i`-th filter are provided in `info.deg[i]`.  If `simple = false` (default), then no simple bases are computed. 

`offset = β` specifies the boundary offset `β` to assess the stability of poles.  Accordingly, for the stability of a continuous-time system all real parts of poles must be at most `-β`,  while for the stability of a discrete-time system all moduli of poles must be at most `1-β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

`smarg = α` specifies the stability margin which defines the stability  domain `Cs` of poles, as follows:  for a continuous-time system, `Cs` is the set of complex numbers  with real parts at most `α`,  while for a discrete-time system, `Cs` is the set of complex numbers with  moduli at most `α < 1` (i.e., the interior of a disc of radius `α` centered in the origin).  If `smarg` is missing, then the employed default values are `α = -β`  for a continuous-time system and `α = 1-β` for a discrete-time system,  where `β` is the boundary offset specified by the keyword argument `offset = β`. 

`sdeg = γ` is the prescribed stability degree for the poles of the filters `Q` and `R`  (default: `γ = -0.05` for the real parts of poles for a continuous-time system and `γ = 0.95` for the magnitudes of poles for a discrete-time system). 

`poles = v` specifies a complex vector `v` containing a complex conjugate set   of desired poles within the stability domain `Cs` to be assigned for the filters `Q` and `R` (default: `poles = missing`).

`tcond = tcmax` specifies the maximum alowed condition number `tcmax`  of the employed non-orthogonal transformations (default: `tcmax = 1.e4`).

`MDtol = tol1` specifies the threshold `tol1` for model detectability checks    (default: `tol1 = 0.0001`).

`MDGainTol = tol2` specifies the threshold `tol2` for strong model detectability checks    (default: `tol2 = 0.01`). 

If `normalize = false` (default), the `i`-th component filter `Q.sys[i]` is scaled such that the minimum gain of `R.sys[i,j]` for `j = 1, ..., N`,   `j` $\neq$ `i`, is equal to one.  If `normalize = true`, the standard normalization of component filters is performed to ensure equal gains for `R.sys[1,j]` and `R.sys[j,1]`.  This option is only possible if `ifilt[1] = 1` (see `MDSelect`).

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` (default) or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of the state-space matrices  `Ai`, `Bi`, `Ci` and `Di`, the absolute tolerance for the nonzero elements of `Ei`,    and the relative tolerance for the nonzero elements of all above matrices.   The default relative tolerance is `ni*ϵ`, where `ϵ` is the working machine epsilon  and `ni` is the orders of the system `sysm.sys[i]`.  The keyword argument `atol3` is an absolute tolerance for observability tests    (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

The resulting named tuple `info` contains `(tcond, degs, MDperf, HDesign)`, where:

`info.tcond` is the maximum of the condition numbers of the employed     non-orthogonal transformation matrices; a warning is issued if `info.tcond >= tcmax`;

`info.degs` is an `N`-dimensional vector, whose `i`-th component is an integer vector  containing the degrees of the basis vectors of the employed simple nullspace basis for the synthesis of the `i`-th filter component, if `simple = true`,  and the degrees of the basis vectors of an equivalent polynomial nullspace basis, if `simple = false`;

`info.MDperf` is an `N × N` array containing the resulting distance-mapping performance,  representing  the peak gains of the associated internal representations of  the model detection filters. If the `(i,j)`-th component filter `R.sys[i,j]`  has the input-output form

```
 rij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,
```

then, the `(i,j)`-th performance gain is evaluated as  `info.MDperf[i,j] = ||Ruij(λ)||∞` if `emdtest = false` (default) or  `info.MDperf[i,j] = ||[Ruij(λ) Rdij(λ)]||∞` if `emdtest = true`.   If `MDfreq = ω`, then each gain `info.MDperf[i,j]` represents the maximum of 2-norm pointwise gains evaluated for all frequencies in `ω`.

`info.HDesign` is an `N`-dimensional vector, whose `i`-th component  is the design matrix `H_i` employed for the synthesis of  the `i`-th model detection filter.

*Method:* The Procedure EMD from [1] is implemented to solve  the exact model detection problem. For more details on  the least order synthesis of model detection filters see [2].

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.2.

[2] A. Varga, Least order fault and model detection using multi-models.         IEEE CDC'09, Shanghai, China, 2009.
