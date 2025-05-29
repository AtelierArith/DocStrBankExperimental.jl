```
application_config(ports::Vector{String}, impl::String, fnames::Vector{String})
```

Convenience constructor for configuring a workflow application with multiple transitions sourcing their implementation details from the same file.

# Arguments

  * `ports::Vector{String}`: List of ports to configure for the workflow transitions.
  * `impl::String`: Julia file containing the implementations called by the workflow transitions.
  * `fnames::Vector{String}`: List of function names to be executed by the workflow transitions.

See also [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
