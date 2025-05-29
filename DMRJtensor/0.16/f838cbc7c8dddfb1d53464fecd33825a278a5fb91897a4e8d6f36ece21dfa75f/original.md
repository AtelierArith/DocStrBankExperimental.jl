```
G = largeMPS(T,Ns[,label="mps_",names=[label*"i" for i = 1:length(psi)],ext=".dmrjulia"])
```

Creates a large MPS type (stored on disk) of element type `T` with `Ns` tensors but does not write anything to disk initially. Filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPO`](@ref) [`largeLenv`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
