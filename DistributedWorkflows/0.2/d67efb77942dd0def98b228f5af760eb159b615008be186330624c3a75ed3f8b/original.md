```
application_config(ports::Vector{String}, impl::Vector{String}, fnames::Vector{String})
```

Constructor for configuring a workflow application with multiple transitions.

# Arguments

  * `ports::Vector{String}`: List of ports to configure for the workflow transitions.
  * `impl::Vector{String}`: List of julia files containing the implementations called by the workflow transitions.
  * `fnames::Vector{String}`: List of function names to be executed by the workflow transitions.

See also [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
