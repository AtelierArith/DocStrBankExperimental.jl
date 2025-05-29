```
G = largeLenv(T,Ns[,label="Lenv_",names=[label*"i" for i = 1:Ns],ext=".dmrjulia"])
```

Creates a large environment type (stored on disk) of element type `T` with `Ns` tensors but does not write anything to disk initially. Filenames specified in `names` (default file extension: `.dmrjulia`)

See also: [`largeMPS`](@ref) [`largeMPO`](@ref) [`largeRenv`](@ref) [`largeEnv`](@ref)
