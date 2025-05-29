```
DefaultFormatter
```

`DefaultFormatter`は、ログメッセージを構築するためにシンプルなフォーマット文字列を使用します。使用する`Record`のフィールドは、中括弧で囲む必要があります。

例) "[{level} | {name}]: {msg}"は、[info | root]: my info messageの形式でメッセージを印刷します。[warn | root]: my warning message. ...
