```
G,K = largeEnv(Ns[,Llabel="Lenv_",Lnames=[label*"i" for i = 1:Ns],Rlabel="Renv_",Rnames=[label*"i" for i = 1:Ns],ext=".dmrjulia",type=Float64])
```

Creates large environments with `Ns` tensors and retrieved through `G` and `K` respectively according to filenames specified in `Lnames` and `Rnames` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref)
