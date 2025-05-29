```
config_session(log::SessionConfig)
config_session(; args...)
```

Set the session for the global FloatTracker configuration instance.

Takes either a `SessionConfig` struct, or the same keyword arguments as the `SessionConfig` constructor.

Passing a partial list of keyword arguments has the same behavior as it does with `config_logger`.
