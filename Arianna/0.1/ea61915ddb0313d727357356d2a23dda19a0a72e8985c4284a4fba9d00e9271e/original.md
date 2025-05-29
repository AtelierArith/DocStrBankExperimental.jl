```
StoreCallbacks{V} <: AriannaAlgorithm
```

Algorithm to store callback values during simulation.

# Fields

  * `callbacks::V`: Vector of callback functions to evaluate
  * `paths::Vector{String}`: Paths to output files for each callback
  * `files::Vector{IOStream}`: File handles for writing callback values
  * `store_first::Bool`: Whether to store callback values at initialization
  * `store_last::Bool`: Whether to store callback values at finalization

# Constructor

```
StoreCallbacks(callbacks::V, path; store_first::Bool=true, store_last::Bool=false)
```

Create a new StoreCallbacks instance.

# Arguments

  * `callbacks::V`: Vector of callback functions
  * `path`: Base path for output files
  * `store_first=true`: Store values at initialization
  * `store_last=false`: Store values at finalization
