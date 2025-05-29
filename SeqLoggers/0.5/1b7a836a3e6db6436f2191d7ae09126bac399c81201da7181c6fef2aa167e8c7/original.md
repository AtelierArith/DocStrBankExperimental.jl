```
load_logger_from_config(file_path::AbstractString)::TeeLogger
```

Create a combined logger from a config file path.

### Note

A combined logger is a `TeeLogger` struct that allows to send the same log message to  all loggers included in the combined logger at once.
