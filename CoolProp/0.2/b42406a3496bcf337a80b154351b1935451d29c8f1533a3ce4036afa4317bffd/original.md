```
get_fluid_param_string(fluid::AbstractString, param::AbstractString)
```

Get a string for a value from a fluid (numerical values for the fluid can be obtained from Props1SI function).

# Arguments

  * `fluid`: The name of the fluid that is part of CoolProp, for instance "n-Propane"
  * `param`: A string, can be in one of the terms described in the following table

| ParamName                     | Description                                                                |
|:----------------------------- |:-------------------------------------------------------------------------- |
| "aliases"                     | A comma separated list of aliases for the fluid                            |
| "CAS", "CAS_number"           | The CAS number                                                             |
| "ASHRAE34"                    | The ASHRAE standard 34 safety rating                                       |
| "REFPROPName", "REFPROP_name" | The name of the fluid used in REFPROP                                      |
| "Bibtex-XXX"                  | A BibTeX key, where XXX is one of the bibtex keys used in get_BibTeXKey    |
| "pure"                        | "true" if the fluid is pure, "false" otherwise                             |
| "formula"                     | The chemical formula of the fluid in LaTeX form if available, "" otherwise |

# Note

A tabular output for this function is available with `?CoolProp_fluids`
