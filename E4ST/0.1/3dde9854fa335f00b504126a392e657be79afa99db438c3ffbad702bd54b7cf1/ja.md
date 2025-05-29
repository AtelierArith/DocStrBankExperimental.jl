```
start_logging!(config)
```

`config[:logging]`に従ってログ記録を開始します。`config[:logging]`の可能なオプション：

  * `true`（デフォルト）：`@info`、`@warning`、および`@error`メッセージを`config[:out_path]/E4ST.log`に記録します
  * `"debug"` - `@debug`、`@info`、`@warning`、および`@error`メッセージを`config[:out_path]/E4ST.log`に記録します
  * `false` - ログ記録なし

ログを記録するには、Logging.jlで定義されている`@info`、`@warn`、または`@debug`を使用できます。また、ヘッダーをログ記録するための便利なメソッド[`log_header`](@ref)を使用することもできます。

ロガーを停止し、そのioストリームを閉じるには、[`stop_logging!(config)`](@ref)を参照してください。
