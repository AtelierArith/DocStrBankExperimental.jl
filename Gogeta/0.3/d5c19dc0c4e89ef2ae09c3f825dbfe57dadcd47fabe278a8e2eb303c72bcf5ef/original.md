```
extract_evotrees_info(evo_model; tree_limit=length(evo_model.trees))
```

Gets the data required for constructing the corresponding MIP from an [EvoTrees](https://github.com/Evovest/EvoTrees.jl) model `evo_model`.  Returns a custom datatype `TEModel` which contains the necessary information.

# Arguments

  * `evo_model`: A trained EvoTrees tree ensemble model.

# Optional arguments

  * `tree_limit`: only first *n* trees specified by the argument will be used
