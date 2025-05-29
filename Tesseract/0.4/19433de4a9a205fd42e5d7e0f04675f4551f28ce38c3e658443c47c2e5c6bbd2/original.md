```
tess_set_param(
    inst::TessInst,
    name::AbstractString,
    value::Float64
)::Bool
```

Sets a `Float64` variable in th Tesseract engine.  Returns `false` if the parameter was not found.

**Arguments:**

| T   | Name  | Default | Description                         |
|:--- |:----- |:------- |:----------------------------------- |
| R   | inst  |         | The instance to set the variable in |
| R   | name  |         | The name of the variable to set.    |
| R   | value |         | The value to set.                   |

**Examples:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_set_param(instance, "classify_min_slope", 0.414214)
true
```

See also: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_get_param`](@ref)
