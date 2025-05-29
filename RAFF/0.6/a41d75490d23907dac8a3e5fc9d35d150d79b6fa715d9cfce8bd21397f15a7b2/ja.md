```
set_lm_output_level(level::LogLevel)
```

[`lmlovo`](@ref)アルゴリズムの出力レベルを希望のログレベルに設定します。オプションは（非常に詳細からエラーのみまで）: `Logging.Debug`, `Logging.Info`, `Logging.Warn` および `Logging.Error` です。パッケージ [`Logging`](https://docs.julialang.org/en/v1.0/stdlib/Logging/index.html) をロードする必要があります。

デフォルトは `Logging.Error` です。
