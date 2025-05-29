```
snoop_bot(config::BotConfig, expression::Expr, test_modul::Module = Main)
```

式を評価することによってプリコンパイルステートメントを生成します。例えば `:(using MyPackage)` のように。補間とマクロはサポートされていません。
