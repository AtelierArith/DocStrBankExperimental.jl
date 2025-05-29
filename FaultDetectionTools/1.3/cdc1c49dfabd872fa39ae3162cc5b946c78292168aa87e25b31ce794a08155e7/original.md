```
S = mdgenspec(sysm::MDMModel; emtest = false, fast = true, MDtol, MDGainTol, MDfreq, 
              sdeg, atol, atol1, atol2, atol3, rtol)
```

Generate for a given multiple synthesis model `sysm::MDMModel` the achievable binary structure matrix `S`  of the internal form corresponding to a set of stable model detection filters, chosen such that the `i`-th residual is  insensitive to the `i`-th model for all control and disturbance inputs.  If `N` is the number of component models, then `S` is an `N×N` binary matrix, whose `(i,i)`-th  element is zero for `i = 1, ..., N`,  and its `(i,j)`-th element is nonzero if there exists a model detection filter such that the corresponding  `i`-th residual is sensitive to the `j`-th model for certain control inputs (if `emtest = false`) or  for certain control and disturbance inputs (if `emtest = true`).   

`MDFreq = freq` specifies a vector of real frequency values or a scalar real frquency value for strong model detectability checks (default: `MDFreq = missing`).

`MDtol = tol1` specifies the threshold `tol1` for model detectability checks    (default: `tol1 = 0.0001`).

`MDGainTol = tol2` specifies the threshold `tol2` for strong model detectability checks    (default: `tol2 = 0.01`). 

The keyword argument `sdeg = β` specifies a prescribed stability degree `β` for the poles of the internally  generated candidate filters, such that the real parts of filters poles must be less than or equal to `β`, in the continuous-time case, and  the magnitudes of filter poles must be less than or equal to `β`, in the discrete-time case. If `sdeg = missing` then no stabilization is performed if `FDFreq = missing`. If `sdeg = missing` and `FDFreq = freq`, then the following default values are employed : `β = -0.05`, in continuous-time case, and  `β = 0.95`,  in discrete-time case. 

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` (default) or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2` and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of the state-space matrices (see below) `Ai`, `Bi`, `Ci` and `Di`, the absolute tolerance for the nonzero elements of `Ei`,    and the relative tolerance for the nonzero elements of all above matrices.   The default relative tolerance is `ni*ϵ`, where `ϵ` is the working machine epsilon  and `ni` is the orders of the system `sysm.sys[i]`.  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 

*Method:* For a multiple synthesis model `sysm` containing `N` stable component models,  the `i`-th component system `sysm.sys[i]` has a descriptor realization of the form  `sysm.sys[i] = (Ai-λEi,Bi,Ci,Di)` and the corresponding input-output form is

```
  yi = Gui(λ)*u + Gdi(λ)*di + Gwi(λ)*wi + Gvi(λ)*vi
```

with the Laplace- or Z-transformed plant outputs `yi`, control inputs `u`,  disturbance inputs `di`, noise inputs `wi`, and auxiliary inputs `vi`,   and with `Gui(λ)`, `Gdi(λ)`, `Gwi(λ)` and  `Gvi(λ)`, the corresponding transfer function matrices. 

To generate the achievable structure matrix `S`, it is assumed that `N` model detection filters are used,  `Q_i(λ)`, for `i = 1, ..., N`, where the `i`-th model detection filter `Q_i(λ)` generates the i-th residual

```
        r_i = Q_i(λ)*| y |
                     | u |
```

and is determined such that it fulfills the nullspace synthesis condition

```
        Q_i(λ)*|Gui(λ) Gdi(λ)| = 0.
               |  I     0    |
```

To generate the elements of the `i`-th row of `S`, the corresponding internal forms of the `i`-th filter  are determined for `j = 1, ..., N` as                    

```
   | Ruij(λ) Rdij(λ) | := Q_i(λ)*| Guj(λ) Gdj(λ) | 
                                 |   I      0    |
```

and `S[i,j]` is set as follows: 

  * if `MDfreq = missing` and `emtest = false`,  then `S[i,j] = 1` if `Ruij(λ) ̸= 0` or `S[i,j] = 0` if `Ruij(λ) = 0`;
  * if `MDfreq = missing` and `emtest = true`,  then `S[i,j] = 1` if `[Ruij(λ) Rdij(λ)] ̸= 0` or `S[i,j] = 0` if `[Ruij(λ) Rdij(λ)] = 0`;
  * if `MDfreq = freq` and `emtest = false`,  then `S[i,j] = 1` if `Ruij(λs) ̸= 0` for any `λs ∈ freq` or       `S[i,j] = 0` if `Ruij(λs) = 0` for all `λs ∈ freq` ;
  * if `MDfreq = freq` and `emtest = true`,  then `S[i,j] = 1` if `[Ruij(λs) Rdij(λs)] ̸= 0` for any `λs ∈ freq` or       `S[i,j] = 0` if `[Ruij(λs) Rdij(λs)] = 0` for all `λs ∈ freq` .

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.2.

[2] A. Varga, Least order fault and model detection using multi-models.         IEEE CDC'09, Shanghai, China, 2009.
