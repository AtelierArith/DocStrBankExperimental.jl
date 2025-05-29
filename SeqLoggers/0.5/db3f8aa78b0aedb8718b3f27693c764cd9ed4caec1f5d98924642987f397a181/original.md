```
load_logger_from_config(config::Dict)::TeeLogger
```

Create a `TeeLoger`, a collection of logger, from a configuration `Dict`.

### Note

  * A `TeeLogger` struct allows to send the same log message  to  all loggers included in the `TeeLoger` at once.
  * The configuration `Dict` requires as `"logging"` field, see example for more details.

### Example

```julia
config = Dict(
    ...,
    "logging" => [
        # logger_type => logger_config_dict,
        "SeqLogger" => Dict(...),
        ...
    ],
    ...
)
```

### Returns

`TeeLogger` as defined in `config`
