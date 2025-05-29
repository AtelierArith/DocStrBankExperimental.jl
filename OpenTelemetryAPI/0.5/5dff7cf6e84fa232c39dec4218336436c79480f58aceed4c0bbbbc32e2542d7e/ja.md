```
Meter(name::String;kw...)
```

Meterは計器を作成する責任があります。

## キーワード引数:

  * `provider::P = global_meter_provider()`
  * `instrumentation_scope = InstrumentationScope()`
