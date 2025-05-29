```
TelegramLogger(tg::TelegramClient; fmt = tg_formatter,
               min_level = Logging.Info, async = true)
```

Telegram チャネルにログメッセージを出力するロガーを作成します。

# 引数

  * `tg`: テレグラムクライアントで、有効な `chat_id` を持っている必要があります。この `chat_id` は結果メッセージに使用されます。
  * `fmt`: (`level`, `_module`, `group`, `id`, `file`, `line`) 引数を受け取り、メッセージプレフィックスを出力する関数。詳細は [Logging](https://docs.julialang.org/en/v1/stdlib/Logging/#Logging.handle_message) モジュールで確認できます。デフォルトでは、各メッセージの前に大文字のレベルが付加されます。例: "INFO: " など。
  * `min_level`: 処理されるログメッセージの最小レベル。
  * `async`: メッセージを `sync` または `async` モードで送信します。テレグラムメッセージの送信には時間がかかる場合があるため、このパラメータを `true` に設定することが理にかなっています。これにより、メッセージはバックグラウンドで送信され、メインプログラムへの影響が少なくなります。しかし、1回の実行でスクリプトのメイン Julia プロセスが非同期メッセージが送信される前に終了する可能性があるため、このパラメータを `false` に設定することも理にかなっています。
  * `silent_errors`: デフォルトでは、メッセージ送信中にエラーが発生した場合、そのエラーは `stderr` チャネルに出力されます。この出力を抑制したい場合は、`silent_errors` を `true` に設定してください。
