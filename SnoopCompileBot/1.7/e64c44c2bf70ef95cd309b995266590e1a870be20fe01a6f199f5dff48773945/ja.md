```
@snoopi_bench config::BotConfig
```

!!! warning
    このマクロは推奨されていません。代わりに関数形式を使用してください: `snoopi_bench(config::BotConfig)`.


テストの推論時間をベンチマークします:

```julia
@snoopi_bench BotConfig("MatLang")
```
