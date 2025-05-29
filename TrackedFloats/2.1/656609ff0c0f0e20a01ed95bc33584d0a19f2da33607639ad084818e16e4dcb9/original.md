```
tf_config_injector(log::InjectorConfig)
tf_config_injector(; args...)
```

Set the injector for the global TrackedFloats configuration instance.

Takes either a `InjectorConfig` struct, or the same keyword arguments as the `InjectorConfig` constructor.

Passing a partial list of keyword arguments has the same behavior as it does with `tf_config_logger`.
