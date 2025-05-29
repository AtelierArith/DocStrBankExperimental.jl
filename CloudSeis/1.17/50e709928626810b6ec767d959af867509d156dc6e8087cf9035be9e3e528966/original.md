```
h = history!([io::CSeis|history::Dict]; kwargs...)
```

Mutate the history of an existing CloudSeis dataset or dictionary, or create a new history dictionary.

# optional key-word arguments

  * `process=""` name of a process that was run in a flow that produced the data-set.
  * `process_parameters=Dict()` process parameters.
  * `flow_parameters=Dit()` flow parameters.

# Notes

  * If more than one process was run (e.g. a flow of processes) to produce the data-set, then call `history!` in the

order that the processes were run.

  * The history can be passed to the `csopen` and `cscreate` methods via the `history` key-word argument.
