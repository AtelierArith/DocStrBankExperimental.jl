```
afdsyn(sysf::FDIModel, SFDI; rdim, nullspace = true, simple = false, minimal = true, exact = false, 
                       gamma = 1, epsreg = 0.1, sdegzer, nonstd = 1, freq, sdeg, smarg, poles, 
                       HDesign, HDesign2, scale2, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true)  
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

Solve the *approximate fault detection and isolation problem* (AFDIP) for a given synthesis model `sysf` with additive faults and a given binary structure vector `SFDI`.  The computed stable and proper filter objects `Q` and `R` contain the  fault detection filter, representing the solution of the AFDIP, and its internal form, respectively,  and are determined such that the transfer function matrix of  `R.sys[:,faults]` has its `j`-th column nonzero if `SFDI[j] = 1`.  If the solution of a strong AFDIP is feasible, then the `j`-th column is zero if `SFDI[j] = 0`.  If only a the solution of a  weak AFDIP is feasible, then the `j`-th column may be nonzero if `SFDI[j] = 0`.  For the description of the keyword parameters see the function [`afdsyn`](@ref). 
