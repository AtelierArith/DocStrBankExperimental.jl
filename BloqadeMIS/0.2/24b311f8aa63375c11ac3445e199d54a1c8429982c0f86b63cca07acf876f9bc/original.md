```
mis_postprocessing(config, graph::AbstractGraph; ntrials::Int=10)
```

The postprocessing protocal used in Harvard experiment for finding MISs: [arxiv:2202.09372](https://arxiv.org/abs/2202.09372), which includes a combination of [`to_independent_set`](@ref) and [`add_random_vertices`](@ref).

# Arguments

  * `config`: configuration to postprocess.
  * `graph`: the problem graph.

# Keyword Arguments

  * `ntrials`: number of trials to use.
