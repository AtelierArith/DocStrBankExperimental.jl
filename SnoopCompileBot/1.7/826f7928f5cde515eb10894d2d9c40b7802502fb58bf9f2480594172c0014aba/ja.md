```
snoop_bot(config::BotConfig, test_modul::Module = Main)
```

パッケージの `runtests.jl` ファイルを使用してプリコンパイルステートメントを生成します。

スヌーピング中、`snoop_bot` はグローバル変数 `SnoopCompile_ENV` を `true` に設定します。必要に応じて、あなたの `runtests.jl` はこの変数の存在と値をチェックして、スヌーピング専用のテスト動作をカスタマイズできます。
