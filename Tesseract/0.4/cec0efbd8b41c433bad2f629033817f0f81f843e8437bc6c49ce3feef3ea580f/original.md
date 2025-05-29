```
tess_params(
    inst::TessInst,
    filename::AbstractString
)::Bool
```

Print out all the parameters with their values and help text to the specified file. Returns false if there was an error.

**Arguments:**

| T   | Name     | Default | Description                                            |
|:--- |:-------- |:------- |:------------------------------------------------------ |
| R   | inst     |         | The Tesseract instance to get get the parameters from. |
| R   | filename |         | The filename to write to.                              |

**Details:**

For each parameter this method prints out it's name, it's value, and some descriptive text about the variable.  Each variable is on it's own line with a tab character seperating each value.

See also: [`tess_params_parsed`](@ref), [`tess_get_param`](@ref), [`tess_set_param`](@ref)
