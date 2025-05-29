```
set_retries(ctx; count=5, all_apis=false)
```

引数:

  * ctx: オプションを設定するためのコンテキスト

キーワード引数:

  * count: 再試行する回数 (デフォルト 5)
  * all_apis: 変更を伴うAPI（例: `put!`）も再試行するかどうか (デフォルト false)
