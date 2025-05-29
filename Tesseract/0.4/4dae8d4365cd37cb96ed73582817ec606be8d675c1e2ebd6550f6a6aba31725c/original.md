```
tess_params(
    inst::TessInst
)::Union{String, Nothing}
```

Print out all the parameters with their values and help text to a string.  Returns `nothing` if there was an error.

**Arguments:**

| T   | Name | Default | Description                                        |
|:--- |:---- |:------- |:-------------------------------------------------- |
| R   | inst |         | The Tesseract instance to get the parameters from. |

**Details:**

The return string will contain multiple lines, each line contains the name of a variable, it's value, and some descriptive text about the variable.  The fields are separated by tabs.

See also: [`tess_params_parsed`](@ref), [`tess_get_param`](@ref), [`tess_set_param`](@ref)
