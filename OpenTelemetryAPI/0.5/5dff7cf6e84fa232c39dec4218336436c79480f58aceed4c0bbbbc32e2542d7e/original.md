```
Meter(name::String;kw...)
```

Meter is responsible for creating instruments.

## Keyword Arguments:

  * `provider::P = global_meter_provider()`
  * `instrumentation_scope = InstrumentationScope()`
