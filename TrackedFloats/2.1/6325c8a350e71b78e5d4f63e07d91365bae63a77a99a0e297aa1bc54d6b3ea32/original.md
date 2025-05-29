```
tf_config_logger(log::LoggerConfig)
tf_config_logger(; args...)
```

Set the logger for the global TrackedFloats configuration instance.

Takes either a `LoggerConfig` struct, or the same keyword arguments as the `LoggerConfig` constructor.

In the case where only a few arguments are specified, it will override only those fields, i.e. the entire LoggerConfig won't be replaced. This is useful, for example, if you need to adjust a field in the middle of a test.
