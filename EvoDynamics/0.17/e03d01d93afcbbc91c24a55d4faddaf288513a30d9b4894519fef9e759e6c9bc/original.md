```
runmodel(param_file::AbstractString; kwargs)
```

Creates and runs a model given `parameters`. Returns a `DataFrame` of collected data, which are specified by `kwargs`.

# Keywords

  * adata=[] agent data to be collected. Either agent fields or functions that accept an agent as input can be put in the array. To aggregate collected data, provide tuples inside the array. For example, to collect mean and median fitness of individuals which is in field `W`, your array will be [(:W,mean), (:W,median)].
  * mdata=[mean*fitness*per*species, species*N] model data to be collected. By default, collects mean population fitness per species. Each row of the output DataFrame corresponds to all agents and each column is the value function applied to a field. The functions in the array are applied to the model object.
  * when=nothing The generations from which data are collected. By default collect at all steps.
  * replicates::Int = 0 Number of replicates per simulation.
  * parallel::Bool = false Whether to run replicates in parallel. If `true`, you should add processors to your julia session (e.g. by `addprocs(n)`) and define your parameters and `EvoDynamics` on all workers. To do that, add `@everywhere` before them. For example, `@everywhere EvoDynamics`.
  * seeds = optionally, provide an array of integers as seeds for each replicate.
  * agentstep=EvoDynamics.agent_step! Define your own agent stepping if you wish to change the sequence of events or change any one event.
  * modelstep=EvoDynamics.model_step!
