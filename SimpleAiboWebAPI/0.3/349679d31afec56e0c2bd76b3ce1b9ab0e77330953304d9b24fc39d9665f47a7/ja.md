```
askSetMode(
  modeName="NORMAL";
  enqueue=false,
  target_deviceID=nothing,
  target_nickname=nothing,
  timeoutLimit=10)
```

`set_mode`を要求します。

  * `askSetMode`は次の文字列のいずれかである必要があります：

      * `NORMAL`
      * `DEVELOPMENT`

このメソッドは、`askAction("set_mode", Dict(ModeName=>modeName, Enqueue=>enqueue))`と同等です。
