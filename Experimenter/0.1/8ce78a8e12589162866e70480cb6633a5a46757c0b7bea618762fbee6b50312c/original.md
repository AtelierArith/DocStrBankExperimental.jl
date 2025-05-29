```
Experiment
```

A database object for storing the configuration options of an experiment.

The signature of the function supplied should be:

```julia
fn(configuration::Dict{Symbol, Any}, trial_id::UUID)
```

The function should be available when including the file provided.

A name is required to uniquely label this experiment.
