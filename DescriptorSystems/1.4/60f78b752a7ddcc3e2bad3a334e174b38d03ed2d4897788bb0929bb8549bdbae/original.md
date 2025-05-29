```
 res = dssubset(sys, subsys, rows, cols; minimal = true, fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ)
```

Assign for a given descriptor system `sys = (A-λE,B,C,D)` its subsystem `sys[row,cols]` to `subsys` and  return the modified system in `res`. `rows` and `cols` are indices, vectors of indices, index ranges, `:` or  any combinations of them. 

If `minimal = true` (default), an irreducible realization of the resulting system `res` is computed, otherwise a possibly non-minimal realization is returned if `minimal = false`. 

The underlying pencil manipulation based minimal realization algorithms employ rank determinations based on either the use of  rank revealing QR-decomposition with column pivoting, if `fast = true`, or the SVD-decomposition. The rank decision based on the SVD-decomposition is generally more reliable, but the involved computational effort is higher.

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of matrices `A`, `B`, `C`, `D`, the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.  The default relative tolerance is `nϵ`, where `ϵ` is the working *machine epsilon*  and `n` is the order of the system `sys`.   The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
