```
submit_workflow(client, workflow, input_params::Vector)
```

Submit a configured workflow to a client instance.

# Arguments

  * `client`: A workflow client instance.
  * `workflow`: A configured workflow object.
  * `input_params::Vector`: List of inputs for the workflow execution.

See also [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
