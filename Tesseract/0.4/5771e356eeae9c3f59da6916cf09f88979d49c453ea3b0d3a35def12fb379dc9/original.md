```
tess_get_param(
    inst::TessInst,
    name::AbstractString,
    ::Type{Bool}
)::Union{Bool, Nothing}
```

Retrieve a boolean parameter from the Tesseract engine.  Returns `nothing` if the value could not be retrieved.

**Arguments:**

| T   | Name         | Default | Description                               |
|:--- |:------------ |:------- |:----------------------------------------- |
| R   | inst         |         | The instance to read the variable from.   |
| R   | name         |         | The name of the variable to read.         |
| R   | ::Type{Bool} |         | Identifies that you want a boolean value. |

**Examples:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_get_param(instance, "edges_debug", Bool)
false
```

See also: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_set_param`](@ref)
