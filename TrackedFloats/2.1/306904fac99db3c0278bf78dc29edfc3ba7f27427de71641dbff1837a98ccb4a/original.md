```
tf_config_session(log::SessionConfig)
tf_config_session(; args...)
```

Set the session for the global TrackedFloats configuration instance.

Takes either a `SessionConfig` struct, or the same keyword arguments as the `SessionConfig` constructor.

Passing a partial list of keyword arguments has the same behavior as it does with `tf_config_logger`.
