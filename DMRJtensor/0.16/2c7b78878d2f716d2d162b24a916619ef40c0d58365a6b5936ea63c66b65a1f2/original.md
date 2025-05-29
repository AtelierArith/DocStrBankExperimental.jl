```
G = largeLenv(lenv[,label="Lenv_",names=[label*"i" for i = 1:length(lenv)],ext=".dmrjulia"])
```

Writes tensors from environment `lenv` to hard disk as retrieved through `G` according to filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
