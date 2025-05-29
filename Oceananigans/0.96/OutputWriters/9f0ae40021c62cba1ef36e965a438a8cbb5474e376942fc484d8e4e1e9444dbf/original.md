```
Checkpointer(model;
             schedule,
             dir = ".",
             prefix = "checkpoint",
             overwrite_existing = false,
             verbose = false,
             cleanup = false,
             properties = default_checkpointed_properties(model))
```

Construct a `Checkpointer` that checkpoints the model to a JLD2 file on `schedule.` The `model.clock.iteration` is included in the filename to distinguish between multiple checkpoint files.

To restart or "pickup" a model from a checkpoint, specify `pickup = true` when calling `run!`, ensuring that the checkpoint file is in directory `dir`. See [`run!`](@ref) for more details.

Note that extra model `properties` can be specified, but removing crucial properties such as `:timestepper` will render restoring from the checkpoint impossible.

The checkpointer attempts to serialize as much of the model to disk as possible, but functions or objects containing functions cannot be serialized at this time.

# Keyword arguments

  * `schedule` (required): Schedule that determines when to checkpoint.
  * `dir`: Directory to save output to. Default: `"."` (current working directory).
  * `prefix`: Descriptive filename prefixed to all output files. Default: `"checkpoint"`.
  * `overwrite_existing`: Remove existing files if their filenames conflict. Default: `false`.
  * `verbose`: Log what the output writer is doing with statistics on compute/write times            and file sizes. Default: `false`.
  * `cleanup`: Previous checkpoint files will be deleted once a new checkpoint file is written.            Default: `false`.
  * `properties`: List of model properties to checkpoint. This list *must* contain               `:grid`, `:particles` and `:clock`, and if using AB2 timestepping then also               `:timestepper`. Default: calls [`default_checkpointed_properties`](@ref) on               `model` to get these properties.
