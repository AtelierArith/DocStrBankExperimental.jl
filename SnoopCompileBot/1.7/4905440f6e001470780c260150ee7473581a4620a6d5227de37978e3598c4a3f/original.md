```
snoop_bot(config::BotConfig, expression::Expr, test_modul::Module = Main)
```

Generate precompile statements by evaluating an expression, for example `:(using MyPackage)`. Interpolation and macros are not supported.
