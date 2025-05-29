```
init_logging(level::LogLevel=Info) -> Nothing
```

MCPサーバーのカスタムMCP形式のロガーでログ記録を初期化します。

# 引数

  * `level::LogLevel=Info`: 表示する最小ログレベル

# 戻り値

  * `Nothing`: 関数はグローバルロガーを設定しますが、値は返しません
