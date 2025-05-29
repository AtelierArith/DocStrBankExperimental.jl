```
fetch_icgem_file(url::AbstractString; kwargs...) -> String
fetch_icgem_file(model::Symbol; kwargs...) -> String
```

Fetch a ICGEM file from the `url` and return its file path to be parsed with the function [`GravityModels.load`](@ref). If the file already exists, it will not be re-downloaded unless the keyword `force = true` is passed.

A symbol can be passed instead the URL to fetch pre-configured gravity field models. The supported values are:

  * `:EGM96`: Earth Gravitational Model from 1996.
  * `:EGM2008`: Earth Gravitational Model from 2008.
  * `:JGM2`: Joint Gravity Model 2.
  * `:JGM3`: Joint Gravity Model 3.

# Examples

```julia-repl
julia> fetch_icgem_file(:EGM96)
[ Info: Downloading the ICGEM file 'EGM96.gfc' from 'http://icgem.gfz-potsdam.de/getmodel/gfc/971b0a3b49a497910aad23cd85e066d4cd9af0aeafe7ce6301a696bed8570be3/EGM96.gfc'...
"/Users/ronan.arraes/.julia/scratchspaces/bd9e9728-6f7b-4d28-9e50-c765cb1b7c8c/icgem/EGM96.gfc"

julia> fetch_icgem_file(:EGM96)
"/Users/ronan.arraes/.julia/scratchspaces/bd9e9728-6f7b-4d28-9e50-c765cb1b7c8c/icgem/EGM96.gfc"
```
