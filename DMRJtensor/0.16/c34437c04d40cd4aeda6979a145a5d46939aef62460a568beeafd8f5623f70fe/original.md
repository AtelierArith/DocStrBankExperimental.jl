```
G = largeRenv(renv[,label="Renv_",names=[label*"i" for i = 1:length(renv)],ext=".dmrjulia"])
```

Writes tensors from environment `renv` to hard disk as retrieved through `G` according to filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeEnv`](@ref)
