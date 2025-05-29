```
S = fdigenspec(sysf::FDIModel; sdeg, FDtol, FDGainTol, FDfreq, atol, atol1, atol2, atol3, rtol, fast = true)
```

Generate all achievable specifications `S` for a given synthesis model `sysf` with additive faults.  Each row of the resulting binary matrix `S` contains a nonzero specification (or fault signature) which can be achieved using a linear fault detection filter (e.g., as obtainable with the help of function [`efdisyn`](@ref)).

`FDFreq = freq` specifies a vector of real frequency values or a scalar real frquency value for strong detectability checks (default: `FDFreq = missing`).

`FDtol = tol1` specifies the threshold `tol1` for assessing weak specifications                       (see also function [`fditspec`](@ref)) (default: `tol1 = 0.0001`).

`FDGainTol = tol2` specifies the threshold `tol2` for assessing strong specifications,   i.e., the threshold for nonzero frequency responce gains for all frequency values specified in `freq` (see also function [`fdisspec`](@ref)) (default: `tol2 = 0.01`). 

The keyword argument `sdeg = β` specifies a prescribed stability degree `β` for the poles of the internally  generated candidate filters, such that the real parts of filters poles must be less than or equal to `β`, in the continuous-time case, and  the magnitudes of filter poles must be less than or equal to `β`, in the discrete-time case. If `sdeg = missing` then no stabilization is performed if `FDFreq = missing`. If `sdeg = missing` and `FDFreq = freq`, then the following default values are employed : `β = -0.05`, in continuous-time case, and  `β = 0.95`,  in discrete-time case. 

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

*Method:* The Procedure GENSPEC from [1] is implemented.  The nullspace method [2] is recursively employed to generate candidate fault detection and isolation filters, whose internal forms provide the structure matrices corresponding to the achievable weak specifications, if `freq = missing`,  or strong specifications for the frequencies conatined in `freq`. The generation method is also described in [3].

*References:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.       Springer Verlag, 2017; sec. 5.4.

[2] A. Varga, On computing nullspace bases – a fault detection perspective.        Proc. IFAC 2008 World Congress, Seoul, Korea, pages 6295–6300, 2008.

[3] A. Varga, On computing achievable fault signatures. Proc. SAFEPROCESS'2009, Barcelona, Spain. 
