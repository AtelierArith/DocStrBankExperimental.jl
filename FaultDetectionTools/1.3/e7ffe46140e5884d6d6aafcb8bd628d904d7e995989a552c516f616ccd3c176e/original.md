```
efdsyn(sysf::FDIModel, S; rdim, nullspace = true, simple = false, minimal = true, 
                       sdeg, smarg, poles, HDesign, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the *exact fault detection and isolation problem* (EFDIP) for a given synthesis model `sysf` with additive faults and a given binary structure vector `S`.  The computed stable and proper filter objects `Q` and `R` contain the  fault detection filter, representing the solution of the EFDIP, and its internal form, respectively, and are determined such that `R.sys[:,faults]` has its `j`-th column nonzero if `S[j] = 1` and the `j`-th column is zero if `S[j] = 0`.  For the description of the keyword parameters see the function [`efdsyn`](@ref). 
