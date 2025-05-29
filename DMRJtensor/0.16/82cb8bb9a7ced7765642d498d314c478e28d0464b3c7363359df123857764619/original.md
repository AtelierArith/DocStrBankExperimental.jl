```
G = largeMPS(psi[,label="mps_",names=[label*"i" for i = 1:length(psi)],ext=".dmrjulia"])
```

Writes tensors from `MPS` `psi` to hard disk as retrieved through `G` according to filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
