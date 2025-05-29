```
tess_params_parsed(
        inst::TessInst
    )::Vector{TessParam}
```

Retrieved all the Tesseract parameters with their valuse as an array of [`TessParam`](@ref) objects.

**Arguments:**

| T   | Name | Default | Description                                        |
|:--- |:---- |:------- |:-------------------------------------------------- |
| R   | inst |         | The Tesseract instance to get the parameters from. |

**Details:**

Parses the result of `[`tess_params`](@ref) into something more easily digested by a computer.  Each line of text is split into 3 values:

  * The name of the parameter.
  * The default value of the parameter (may be an empty string).
  * Text describing the parameter.

Each value is separated by a tab and the description is terminated by a new line.

See also: [`TessParam`](@ref), [`tess_params`](@ref), [`tess_get_param`](@ref),           [`tess_set_param`](@ref)
