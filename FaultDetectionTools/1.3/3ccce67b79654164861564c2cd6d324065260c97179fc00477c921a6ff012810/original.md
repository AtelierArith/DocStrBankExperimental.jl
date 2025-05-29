```
fdichkspec(sysf::FDIModel, SFDI::BitMatrix; sdeg, FDtol, FDGainTol, FDfreq, 
             atol, atol1, atol2, atol3, rtol, fast = true, minimal = false) -> (rdims, orders, leastorders)
```

Check for a given synthesis model `sysf::FDIModel` the feasibility of a set of fault detection and isolation specifications `SFDI`.  If `SFDI` has `N` rows (i.e., contains `N` specifications), then the `N`-dimensional integer vectors `rdims`, `orders`, `leastorders`  are returned and contain information related to the synthesis of FDI filters to achieve the feasible specifications.  For the `i`-th specification contained in `SFDI[i,:]`, `rdims[i]` contains the number of residual  outputs of a minimal nullspace basis based FDI filter which can be used to achieve this specification.  If `rdims[i] = 0`, then the `i`-th specification is not feasible. For a feasible `i`-th specification, `orders[i]`  contains the order of the minimal nullspace basis based FDI filter which can be used to achieve this specification.  If the `i`-th specification is not feasible, then `orders[i]` is set to `-1`. If `minimal = true`, `leastorders[i]` contains the least achievable order for a scalar output FDI filter which can be used   to achieve the `i`-th specification. If `minimal = false` or if the `i`-th specification is not  feasible, then `leastorders[i]` is set to `-1`.

`FDFreq = freq` specifies a vector of real frequency values or a scalar real frquency value for strong detectability checks (default: `FDFreq = missing`).

`FDtol = tol1` specifies the threshold `tol1` for assessing weak specifications                       (see also function [`fditspec`](@ref)) (default: `tol1 = 0.0001`).

`FDGainTol = tol2` specifies the threshold `tol2` for assessing strong specifications,   i.e., the threshold for nonzero frequency responce gains for all frequency values specified in `freq` (see also function [`fdisspec`](@ref)) (default: `tol2 = 0.01`). 

The keyword argument `sdeg = β` specifies a prescribed stability degree `β` for the poles of the internally  generated candidate filters, such that the real parts of filters poles must be less than or equal to `β`, in the continuous-time case, and  the magnitudes of filter poles must be less than or equal to `β`, in the discrete-time case. If `sdeg = missing` then no then no stabilization is performed if and `FDFreq = missing`. If `sdeg = missing` and `FDFreq = freq`, then the fllowing default values are employed : `β = -0.05`, in continuous-time case, and  `β = 0.95`,  in discrete-time case. 

The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `n*ϵ`, where `ϵ` is the working machine epsilon  and `n` is the order of the system `sysf.sys`.  The keyword argument `atol3` is an absolute tolerance for observability tests (default: internally determined value).  The keyword argument `atol` can be used  to simultaneously set `atol1 = atol`, `atol2 = atol` and `atol3 = atol`. 

*Method:* The nullspace method of [1] is successively employed to  determine FDI filters as minimal left nullspace bases which solve  suitably formulated fault detection problems. 

*References:*

[1] A. Varga, On computing nullspace bases – a fault detection perspective.        Proc. IFAC 2008 World Congress, Seoul, Korea, pages 6295–6300, 2008.
