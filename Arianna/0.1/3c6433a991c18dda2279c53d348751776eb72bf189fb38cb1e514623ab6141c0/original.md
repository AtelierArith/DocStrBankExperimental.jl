```
StoreBackups <: AriannaAlgorithm
```

Algorithm to create backup files of system states during simulation.

# Fields

  * `dirs::Vector{String}`: Directories for storing backup files
  * `fmt::Format`: Format type for output files
  * `store_first::Bool`: Whether to store backups at initialization
  * `store_last::Bool`: Whether to store backups at finalization
