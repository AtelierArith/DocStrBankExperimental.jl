```
struct InitData{T} <: AbstractInitData
```

Initialization data type for the inclusion of initial data before the first horizon. The standard initialization data is using a single value for a given variable. Multiple variables can be initialized simultaneously.

# Fields

  * **`init_val_dict::Dict{Symbol,T}`** is a dictionary with the variable symbol as key and the value in the beginning of the analysis as value.
