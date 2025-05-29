```
workflow_config(workflow::String, output_dir::String, app_config::Vector{Application_config})
```

Configures a workflow for execution by a client instance.

# Arguments

  * `workflow::String`: Name of the workflow.
  * `output_dir::String`: Location to store any output data generated during the workflow execution.
  * `app_config::Vector{Application_config}`: List of application configurations for the workflow exeuction.

See also [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
