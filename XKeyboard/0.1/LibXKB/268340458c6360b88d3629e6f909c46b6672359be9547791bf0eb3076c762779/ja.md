```
xkb_context_set_log_level(context, level)
```

現在のログレベルを設定します。

デフォルトのレベルは XKB*LOG*LEVEL*ERROR です。コンテキストが作成された時に設定された環境変数 XKB*LOG_LEVEL は、デフォルト値を上書きします。レベル番号または名前として指定できます。

xkb_context

### パラメータ

  * `context`: ログレベルを設定するコンテキスト。
  * `level`: 使用するログレベル。このレベルおよびそれ以下のメッセージのみがログに記録されます。
