```
@snoopi_bench config::BotConfig
```

!!! warning
    This macro isn't recommend. Use the function form instead: `snoopi_bench(config::BotConfig)`.


Benchmarking the infer time of the tests:

```julia
@snoopi_bench BotConfig("MatLang")
```
