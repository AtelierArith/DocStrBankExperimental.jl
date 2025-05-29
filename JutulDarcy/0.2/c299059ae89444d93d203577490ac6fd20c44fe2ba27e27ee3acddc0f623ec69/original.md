```
setup_reservoir_simulator(models, initializer, parameters = nothing; <keyword arguments>)
```

# Arguments

  * `models`: either a single model or a Dict with the key :Reservoir for multimodels
  * `initializer`: used to setup state0, must be compatible with `model`
  * `parameters`: initialized parameters, must be compatible with `model` if provided

# Keyword arguments

  * `split_wells`: Add facility model to each well (needed for domain decomposition and MPI solves)
  * `assemble_wells_together`: Option to split wells into multiple sparse matrices (false argument experimental)
  * `specialize=false`: use deep specialization of storage for faster execution, but significantly more compile time

Additional keyword arguments are documented in the version of this function that uses `JutulCase` as the input.
