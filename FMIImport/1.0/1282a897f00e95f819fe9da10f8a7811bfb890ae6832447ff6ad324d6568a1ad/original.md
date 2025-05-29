```
loadFMU(pathToFMU; unpackPath, cleanup, type)
```

Loads an FMU, independent of the used FMI-version (the version is checked during unpacking the archive).

# Arguments

  * `path::String` the path pointing on the FMU file.

# Keywords

  * `unpackPath::Union{String, Nothing}=nothing` the optional unpack path, if `nothing` a temporary directory depending on the OS is picked.
  * `cleanup::Bool=true` a boolean indicating whether the temporary directory should be cleaned automatically.
  * `type::Union{Symbol, Nothing}=nothing` the type of FMU (:CS, :ME, :SE), if multiple types are available. If `nothing` one of the available types is chosen automatically with the priority CS > ME > SE.
