```
snoop_bench(config::BotConfig, expression::Expr, test_modul::Module = Main)
```

Benchmark your precompile files by evaluating an expression, for example `:(using MyPackage)`. Interpolation and macros are not supported.
