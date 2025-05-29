```
G = largeLenv(Ns[,label="Lenv_",names=[label*"i" for i = 1:Ns],ext=".dmrjulia"])
```

Creates a large environment type (stored on disk) with `Ns` tensors (element type: Float64) but does not write anything to disk initially. Filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
