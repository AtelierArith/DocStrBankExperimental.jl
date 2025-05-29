```
tess_get_param(
    inst::TessInst,
    name::AbstractString,
    ::Type{T}
)::Union{T, Nothing} where T<:Integer
```

Retrieve an integer parameter from the Tesseract engine.  Returns `nothing` if the value could not be retrieved.

**Arguments:**

| T   | Name      | Default | Description                              |
|:--- |:--------- |:------- |:---------------------------------------- |
| R   | inst      |         | The instance to read the parameter from. |
| R   | name      |         | The name of the parameter to read.       |
| R   | ::Type{T} |         | The type to return.                      |

**Examples:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_get_param(instance, "edges_min_nonhole", Int)
12
```

See also: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_set_param`](@ref)
