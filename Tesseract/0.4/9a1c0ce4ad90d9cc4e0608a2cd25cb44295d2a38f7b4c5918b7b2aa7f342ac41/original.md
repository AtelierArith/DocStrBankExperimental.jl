```
struct TessParam{T}
    name::String
    default::T
    desc::String
    debug::Bool
end
```

Holds details about the default value of a parameter.

**Values:**

| Name    | Description                             |
|:------- |:--------------------------------------- |
| name    | The name/ID of the parameter.           |
| default | The default value of the parameter.     |
| desc    | The description of the variable.        |
| debug   | True if the value is a debug parameter. |

**Details:**

This structure currently comes in 3 flavors, T may be Float64, Int32, or a String based on the default value.

See also: [`tess_params_parsed`](@ref), [`tess_get_param`](@ref), [`tess_set_param`](@ref)
