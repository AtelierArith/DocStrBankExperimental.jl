```
G = largeMPO(mpo[,label="mpo_",names=[label*"i" for i = 1:length(mpo)],ext=".dmrjulia"])
```

Writes tensors from `MPO` `mpo` to hard disk as retrieved through `G` according to filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
