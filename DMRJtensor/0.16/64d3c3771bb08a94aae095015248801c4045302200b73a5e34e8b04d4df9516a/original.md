```
G = largeMPO(Ns[,label="mpo_",names=[label*"i" for i = 1:length(mpo)],ext=".dmrjulia"])
```

Creates a large MPO type (stored on disk) with `Ns` tensors (element type: Float64) but does not write anything to disk initially. Filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
