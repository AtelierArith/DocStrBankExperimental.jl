```
@snoopi_bot config::BotConfig
```

!!! warning
    このマクロは推奨されません。代わりに関数形式を使用してください: `snoopi_bot(config::BotConfig)`.


スヌーピングのためのテストを使用します:

```julia
@snoopi_bot BotConfig("MatLang")
```
