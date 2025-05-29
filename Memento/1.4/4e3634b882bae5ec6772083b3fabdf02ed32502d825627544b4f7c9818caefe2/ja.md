```
Record
```

`Symbol` キーを持つ辞書のようなコンテナで、msg、date、level、stacktrace などのログイベントに関する情報を格納します。`Formatter` は `Records` を使用してログメッセージ文字列をフォーマットします。

`Record` のプロパティには `getproperty` を使用してアクセスできます（例: record.msg）。

`Record` のサブタイプは `getproperty(::MyRecord, ::Symbol)` とキー-バリュー ペアの反復を実装する必要があります。
