```
client(workers::Int, nodefile::String, rif_strategy::String, log_host::String, log_port::Int)
```

Configures and starts a client setting up the workflow execution infrastructure and connects to a logging service. The nodefile will be automatically populated with the local host name if it doesn't exist in the given location or the `rif_strategy` is `local`.

# Arguments

  * `workers::Int`: Number of workers launched per node.
  * `nodefile::String`: Location of the nodefile.
  * `rif_strategy::String`: Launch mode of the workflow infrastructure. Accepts `ssh` for distributing the workers across multiple nodes or `local` for running on the localhost only.
  * `log_host::String`: Host of the logging service.
  * `log_port::Int` : Port the logging service is listening on.

See also [`Workflow_PetriNet`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
