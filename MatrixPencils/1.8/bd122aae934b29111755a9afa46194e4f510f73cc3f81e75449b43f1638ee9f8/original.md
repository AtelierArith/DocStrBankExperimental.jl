```
eigselect1(ev, sdeg, evref, disc; cflag) -> (γ, evupd)
```

Select a real or complex eigenvalue `γ` to be assigned from a given set of eigenvalues  in the vector `ev`. The resulting `evupd` contains the remaining eigenvalues from `ev`. The selected eigenvalue `γ` is the nearest one to the reference value `evref`.  If `ev = missing` and `disc = false`, then, if `cflag = false` (in the real case) `γ` is set equal to the  desired stability degree `sdeg`, while if `cflag = true` (in the complex case) `γ` is set  `γ = sdeg + im*imag(evref)`.  If `ev = missing` and `disc = true`, then, if `cflag = false` (in the real case) `γ` is set equal to the  desired stability degree `sdeg`, while if `cflag = true` (in the complex case) `γ` is set  `γ = sdeg/abs(evref))*evref`.  If `ev = missing` and `sdeg = missing`, then `γ = nothing`. 
