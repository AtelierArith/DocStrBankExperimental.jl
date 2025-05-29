```
setrecord!(logger::Logger, rec::Type{R}) where {R<:Record}
```

ロガーのレコードタイプを設定します。

# 引数

  * `logger::Logger`: 設定するロガー。
  * `rec::Record`: メッセージをログするために使用する `Record` タイプ（例: `DefaultRecord`）。
