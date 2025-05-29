```
config_injector(log::InjectorConfig)
config_injector(; args...)
```

Set the injector for the global FloatTracker configuration instance.

Takes either a `InjectorConfig` struct, or the same keyword arguments as the `InjectorConfig` constructor.

Passing a partial list of keyword arguments has the same behavior as it does with `config_logger`.
