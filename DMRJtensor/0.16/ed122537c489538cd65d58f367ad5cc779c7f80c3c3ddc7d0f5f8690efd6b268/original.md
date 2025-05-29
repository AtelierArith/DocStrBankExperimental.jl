```
G,K = largeEnv(lenv,renv[,Llabel="Lenv_",Lnames=[label*"i" for i = 1:length(psi)],Rlabel="Renv_",Rnames=[label*"i" for i = 1:length(renv)],ext=".dmrjulia",type=Float64])
```

Writes tensors from environments `lenv` and `renv` to hard disk as retrieved through `G` and `K` respectively according to filenames specified in `Lnames` and `Rnames` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref)
