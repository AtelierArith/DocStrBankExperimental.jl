```
kick_start_compat(
    code_dir::String,
    julia_version = "1.5.4";
    exact_versions = false
)
```

Project.toml と Manifest.toml の両方を含むディレクトリを指定すると、すべての Project.toml 依存関係のための推奨 compat エントリの文字列を出力します。印刷される compat エントリがマニフェストファイルと正確に一致するようにするには、`exact_versions = true` を設定してください。
