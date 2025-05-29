```
application_config(port::String, impl::String, fname::String)
```

Convenience constructor for configuring a workflow application with a single transition.

# Arguments

  * `ports::String`: Ports to configure for the workflow transition.
  * `impl::String`: Julia file containing the implementation called by the workflow transition.
  * `fnames::String`: Function name to be executed by the workflow transition.

See also [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
