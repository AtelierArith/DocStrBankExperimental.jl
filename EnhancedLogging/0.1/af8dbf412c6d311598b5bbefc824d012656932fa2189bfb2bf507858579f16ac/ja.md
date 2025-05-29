```
EnhancedConsoleLogger(stream::IO==stderr; kwargs...)
```

標準ライブラリの `ConsoleLogger` の置き換えで、いくつかの使いやすさの改善が加えられています。

# 追加のキーワード引数

`EnhancedConsoleLogger` は `ConsoleLogger` が受け入れるすべての標準キーワード引数をサポートしています。さらに、以下の引数に対して特別な動作が定義されています：

  * `_pid`: ログメッセージの右上隅に列として印刷します。このキーワードは、ログメッセージの発信元プロセスを表示するために `WorkerLogger` によって内部的に使用されます。
  * `_overwrite`: `true` の場合、ログメッセージの繰り返しが上書きされて印刷され、画面がログメッセージで埋まるのを避けます。
  * `progress`: 0 と 1 の間の進捗に対して、ログメッセージの右側に進捗バーを描画します。
  * `_showlocation`: `true` の場合、ログメッセージの位置を印刷します。`Debug`、`Warning`、および `Error` ログではデフォルトで `true` になり、`Info` ログでは `false` になります。
