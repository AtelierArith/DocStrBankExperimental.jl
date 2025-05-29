```
tess_get_param(
    inst::TessInst,
    name::AbstractString,
    ::Type{String}
)::Union{String, Nothing}
```

Retrieve a String parameter from the Tesseract engine.  Returns `nothing` if the value could not be retrieved.

**Arguments:**

| T   | Name            | Default | Description                               |
|:--- |:--------------- |:------- |:----------------------------------------- |
| R   | inst            |         | The instance to read the variable from.   |
| R   | name            |         | The name of the parameter to read.        |
| R   | ::Type{Float64} |         | Identifies that you want a Float64 value. |

**Examples:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_get_param(instance, "page_separator", String)
"\f"
```

See also: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_set_param`](@ref)
