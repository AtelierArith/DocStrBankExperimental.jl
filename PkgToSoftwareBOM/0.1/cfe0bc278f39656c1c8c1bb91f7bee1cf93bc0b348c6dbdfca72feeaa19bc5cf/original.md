```
generateSPDX(docData::spdxCreationData= spdxCreationData(), sbomRegistries::Vector{<:AbstractString}= ["General"])
```

Generate a software BOM in the SPDX format. By default, the SBOM will describe all the packages and artifacts in the active environment using the General registry to retrieve download information.

If you would like to use a different registry or search multiple registries, you just call `generateSPDX` with two arguments.

For example to create a User Environment SBOM using the General registry and another registry called "PrivateRegistry", type:

```julia-repl
sbom= generateSPDX(spdxCreationData(), ["PrivateRegistry", "General"]);
```
