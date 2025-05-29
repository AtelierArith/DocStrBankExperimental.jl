```
tess_set_debug_param(
    inst::TessInst,
    name::AbstractString,
    value::AbstractString
)::Bool
```

Sets a debug string variable in th Tesseract engine.  Returns `false` if the parameter was not found.

**Arguments:**

| T   | Name  | Default | Description                         |
|:--- |:----- |:------- |:----------------------------------- |
| R   | inst  |         | The instance to set the variable in |
| R   | name  |         | The name of the variable to set.    |
| R   | value |         | The value to set.                   |

**Details:**

If the parameter is not a debug setting then the value will not be changed.

**Examples:**

```jldoctest
julia> using Tesseract

julia> download_languages()
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_set_debug_param(instance, "debug_file", "debug.log")
true
```

See also: [`tess_params`](@ref), [`tess_params_parsed`](@ref), [`tess_get_param`](@ref)
