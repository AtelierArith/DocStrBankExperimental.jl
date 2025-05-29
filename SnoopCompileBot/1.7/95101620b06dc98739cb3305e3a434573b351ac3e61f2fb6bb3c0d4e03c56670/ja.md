```
snoop_bench(config::BotConfig, test_modul::Module = Main)
```

パッケージの `runtests.jl` ファイルを使用して、プリコンパイルファイルのベンチマークを行います。

スヌーピング中、`snoop_bench` はグローバル変数 `SnoopCompile_ENV` を `true` に設定します。必要に応じて、`runtests.jl` でこの変数の存在と値をチェックして、スヌーピング専用にテストの動作をカスタマイズできます。```
