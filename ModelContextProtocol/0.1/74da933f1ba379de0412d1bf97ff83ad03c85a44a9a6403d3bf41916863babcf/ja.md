```
MCPLogger(stream::IO=stderr, level::LogLevel=Info) -> MCPLogger
```

指定されたストリームとレベルで新しいMCPLoggerインスタンスを作成します。

# 引数

  * `stream::IO=stderr`: ログメッセージが書き込まれる出力ストリーム
  * `level::LogLevel=Info`: 表示する最小ログレベル

# 戻り値

  * `MCPLogger`: 新しいロガーインスタンス
