```
set_raff_output_level(level::LogLevel)
```

Set the output level of [`raff`](@ref) and [`praff`](@ref) algorithms to the desired logging level. Options are (from highly verbose to just errors): `Logging.Debug`, `Logging.Info`, `Logging.Warn` and `Logging.Error`. The package [`Logging`](https://docs.julialang.org/en/v1.0/stdlib/Logging/index.html) needs to be loaded.

Defaults to `Logging.Error`.
