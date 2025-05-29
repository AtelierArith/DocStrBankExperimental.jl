```
C_iio_create_scan_context(backend, flags)
```

スキャンコンテキストを作成します。

# パラメータ

  * `backend::String` : スキャンに使用するバックエンドを含むNULL終端文字列（例：バージョン0.20以前："local"、"ip"、または"usb"；バージョン0.20以降は、"local:usb:"、"ip:usb:"、"local:usb:ip:"など複数を扱うことができます）。NULLの場合、すべての利用可能なバックエンドが使用されます。
  * `flags::UInt32` : 現在は未使用。0に設定します。

# 戻り値

  * 成功した場合、`iio_scan_context`構造体へのポインタ
  * 失敗した場合、NULLが返され、errnoが適切に設定されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#gaa333dd2e410a2769cf5685019185d99c)
