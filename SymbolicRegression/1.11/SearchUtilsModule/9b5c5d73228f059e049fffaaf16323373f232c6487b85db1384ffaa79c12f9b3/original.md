```
RuntimeOptions{PARALLELISM,DIM_OUT,RETURN_STATE,LOGGER} <: AbstractRuntimeOptions
```

Parameters for a search that are passed to `equation_search` directly, rather than set within `Options`. This is to differentiate between parameters that relate to processing and the duration of the search, and parameters dealing with the search hyperparameters itself.
