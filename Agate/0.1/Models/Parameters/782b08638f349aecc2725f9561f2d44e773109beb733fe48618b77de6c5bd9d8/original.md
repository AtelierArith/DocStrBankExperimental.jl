```
compute_allometric_parameters(plankton::Dict) -> Dict
```

This function:     - generates `n` names for each `plankton` group (e.g., "P", "Z" or "cocco") of the form:       `["P1", ..., "P<n>", "Z1", ...., "Z<n>", ...]`     - generates `n` diameters for each `plankton` group using either a linear or a log       splitting scale     - optionally computes emergent parameters (allometric functions, assimilation matrix,       palatability matrix) for each group-diameter combination     - reshapes any other group specific parameters to a NamedArray (e.g., `linear_mortality`)

All parameters are returned as:     `Dict(<parameter> => <NamedArray of values>, ....)` using either the group names (e.g., "P") or names generated in the first step (e.g., "P1").

# Arguments

  * `plankton`: a Dictionary of plankton groups' specific parameters of the form:      `Dict(<group name> => Dict(<parameter> => <value>, ....), ...)`

    The Dictionary for each group (e.g., "P", "Z" or "cocco") has to contain at least the   keys "n" and "diameters", which are either an array of values or a dictionary of the   following form:       `Dict(           "P" => Dict(               "n" => 2,               "diameters" =>                   Dict("min_diameter" => 1, "max_diameter" => 10, "splitting" => "log_splitting"),               ...               ),           "Z" => ...       )`

    The Dictionary for each group can optionally include the following keys and values:       - key: "allometry" (compute diameter dependent parameters)           - value: Dictionary of the form               `Dict(<param name> => Dict("a" => <value>, "b" => <value>), ...)`       - key: "palatability" (generate a palatability matrix)           - value: Dictionary with "can*eat", "optimum*predator*prey*ratio", "protection",             "specificity" keys       - key: "assimilation*efficiency" (generate assimilation efficiency matrix)           - value: Dictionary with "can*eat", "can*be*eaten", "assimilation*efficiency" keys   For example:       ```       Dict(           "P" => Dict(               ...,               "allometry" => Dict(                   "maximum*growth*rate" => Dict("a" => 2.3148e-5, "b" => -0.15),                   "nutrient*half*saturation" => Dict("a" => 0.17, "b" => 0.27),               ),               ...           ),           "Z" => Dict(               ...,               "palatability" => Dict(                   "can*eat" => 1,                   "optimum*predator*prey*ratio" => 10,                   "protection" => 1,                   "specificity" => 0.3,               ),               "assimilation*efficiency" => Dict(                   "can*be*eaten" => 0,                   "can*eat" => 1,                   "assimilation*efficiency" => 0.32               ),               ...           )       )       ```
