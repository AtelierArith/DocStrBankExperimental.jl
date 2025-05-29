```
ModelHierarchy(root_parts,model,num_procs_x_level)
```

  * `root_parts`: Initial communicator. Will be used to generate subcommunicators.
  * `model`: Initial refinable distributed model. Will be set as coarsest level.
  * `num_procs_x_level`: Vector containing the number of processors we want to distribute   each level into. We need `num_procs_x_level[end]` to be equal to    the number of parts of `model`, and `num_procs_x_level[1]` to lower than the total    number of available processors in `root_parts`.
