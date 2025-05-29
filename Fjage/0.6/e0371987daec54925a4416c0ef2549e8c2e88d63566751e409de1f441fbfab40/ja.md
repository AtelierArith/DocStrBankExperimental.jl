```
msg = Message([perf])
msg = Message(inreplyto[, perf])
```

パフォーマティブ（`perf`）のみを持ち、データを持たないメッセージを作成します。パフォーマティブが指定されていない場合、デフォルトはINFORMです。`inreplyto`が指定されている場合、メッセージの`inReplyTo`および`recipient`フィールドはそれに応じて設定されます。
