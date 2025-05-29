```
abstract type WebsocketError <: Exception
```

WebsocketError の子エラータイプには、以下のフィールドがあります：

  * msg::String
  * log::Function

`log()` 関数は内部的に次のように呼び出されます: @error msg  exception = (err, trace)

ここで `trace` は例外の発生元のバックトレースです。
