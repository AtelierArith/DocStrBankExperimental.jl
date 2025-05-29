```
snoop_bench(config::BotConfig, expression::Expr, test_modul::Module = Main)
```

式を評価することでプリコンパイルファイルのベンチマークを行います。例えば `:(using MyPackage)` のようにします。補間やマクロはサポートされていません。
