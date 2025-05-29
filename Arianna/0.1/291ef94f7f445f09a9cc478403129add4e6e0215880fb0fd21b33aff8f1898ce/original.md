```
StoreParameters{V<:AbstractArray} <: AriannaAlgorithm
```

A struct representing a parameter store.

# Fields

  * `paths::Vector{String}`: Vector of paths to the parameter files
  * `files::Vector{IOStream}`: Vector of open file streams to the parameter files
  * `parameters_list::V`: List of parameters to store
  * `store_first::Bool`: Flag to store the parameters at the first step
  * `store_last::Bool`: Flag to store the parameters at the last step

# Type Parameters

  * `V`: Type of the parameter array
